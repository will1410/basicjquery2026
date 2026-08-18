# Basic jQuery for Koha

## Koha customization

### What does jQuery have to do with Koha?

Koha has four system preferences that allow users to add JavaScript and jQuery to the OPAC

### What are those 4 system preferences?

- IntranetUserJS (adds JavaScript and jQuery to the staff client)
- OPACUserJS (adds JavaScript and jQuery to the OPAC)
- SCOUserJS (adds JavaScript and jQuery to the self-checkout system)
- SelfCheckInUserJS (adds JavaScript and jQuery to the self check-in system)

## Summary so far:

- _You can use jQuery to modify the way Koha looks and operates without having to do a development_

---

### What is jQuery?

jQuery is a JavaScript library

For more information, see:

https://jquery.com/

https://www.w3schools.com/jquery/


### What's a JavaScript library?

A library (in this context) is a set of pre-defined functions that can be accessed through a short-hand or abbreviated process

#### Javascript example:

~~~JavaScript
document.getElementById("selector").style.display = "none";
~~~

#### jQuery example:

~~~JavaScript
$('selector').hide();
~~~

## Summary so far:

- _jQuery is simplified JavaScript that anyone can learn_
- _You can use jQuery to modify the way Koha looks and operates without having to do a development_

---

### Basic components:

jQuery statements should start with dollar sign and end with a semicolon 


$ ;


---

Selectors are inside of quotes inside of parentheses


('')


---

Events start with a . and are followed by something in parentheses


.()


---

Put it all together and you get a basic skeleton for a piece of jQuery


$('').();


---

### What is a selector?

A selector is the HTML element that tells jQuery which HTML element that jQuery is going to modify

### What is an HTML element?

HTML elements are the parts of a web page that tell your browser how to display the page

~~~html
<p>, <table>, <h1>, <h2>, <h3>, <h4>, <h5>, <h6>, <input>,
~~~ 

etc. are some examples of HTML tags and elements

Sometimes tags also contains classes or ids that help identify specific elements or classes of elements

## Summary so far:

- _You can use jQuery to modify the way Koha looks and operates without having to do a development_
- _jQuery is simplified JavaScript that anyone can learn_
- _A selector tells jQuery which part of the page to modify_

---

### What is an event, effect, or method?

Some useful events are .click(), .hover(), .toggle(), .resize()

Some simple effects are .fadeIn(), .fadeOut(), .hide(), and .show()

Some simple methods are .append(), .prePend(), .addClass(), .html(), and dozens others

## Summary so far:

- _You can use jQuery to modify the way Koha looks and operates without having to do a development_
- _jQuery is simplified JavaScript that anyone can learn_
- _A selector tells jQuery which part of the page to modify_
- _An event, effect, or method tells jQuery what to do to the selected element_

---

### How do I find a selector?

If you are using Firefox or Chrome, type ctrl-shift-i to open the developer tools.

### Document ready function

See https://wiki.koha-community.org/wiki/JQuery_Library

Your jQuery goes between the {} 

~~~javascript
$(document).ready(function() { 
// YOUR CODE GOES HERE //
});
~~~

## Examples

### Example - selecting by class

Make the "My account" drop-down disappear on all pages

~~~javascript
$('.toplinks-myaccount').hide();
~~~

---

Make the "My checkouts" drop-down disappear on all pages

~~~javascript
$('.toplinks-mycheckouts').hide();
~~~

---

Make the "Set library" drop-down disappear on all pages

~~~javascript
$('.toplinks:contains("Set library")').hide();
~~~

---

### Selecting by ID

Make the subtype limits disappear on the advanced search page

~~~javascript
$('#subtype').hide();
~~~

---

### Make the branch drop-down disappear on the login page

~~~javascript
$('#main_auth #branch').hide();
~~~

## This looks more complex, but it's not - it's just long

### Add descriptions to biblio tabs

~~~javascript
//Home > Cataloging > Editing [TITLE INFORMATION]
//(/cgi-bin/koha/cataloguing/addbiblio.pl?biblionumber=[BIBLIONUMBER]
//Home > Cataloging > Add MARC record
//(/cgi-bin/koha/cataloguing/addbiblio.pl?frameworkcode=)
  //BEGIN Add labels to Marc tabs
    $('#cat_addbiblio .toolbar-tabs-container a[href="#tab0XX_panel"]').append('<br>Control<br>and<br>coded fields');
    $('#cat_addbiblio #tab0XX_panel h3').append(' - Control and coded fields');
    $('#cat_addbiblio .toolbar-tabs-container a[href="#tab1XX_panel"]').append('<br>Main entry');
    $('#cat_addbiblio #tab1XX_panel h3').append(' - Main entry');
    $('#cat_addbiblio .toolbar-tabs-container a[href="#tab2XX_panel"]').append('<br>Title<br>and<br>edition');
    $('#cat_addbiblio #tab2XX_panel h3').append(' - Title and edition');
    $('#cat_addbiblio .toolbar-tabs-container a[href="#tab3XX_panel"]').append('<br>Physical description');
    $('#cat_addbiblio #tab3XX_panel h3').append(' - Physical description');
    $('#cat_addbiblio .toolbar-tabs-container a[href="#tab4XX_panel"]').append('<br>Series');
    $('#cat_addbiblio #tab4XX_panel h3').append(' - Series');
    $('#cat_addbiblio .toolbar-tabs-container a[href="#tab5XX_panel"]').append('<br>Notes');
    $('#cat_addbiblio #tab5XX_panel h3').append(' - Notes');
    $('#cat_addbiblio .toolbar-tabs-container a[href="#tab6XX_panel"]').append('<br>Subject access');
    $('#cat_addbiblio #tab6XX_panel h3').append(' - Subject access');
    $('#cat_addbiblio .toolbar-tabs-container a[href="#tab7XX_panel"]').append('<br>Added<br>and<br>linking entry');
    $('#cat_addbiblio #tab7XX_panel h3').append(' - Added and linking entry');
    $('#cat_addbiblio .toolbar-tabs-container a[href="#tab8XX_panel"]').append('<br>Series added entry<br>and<br>electronic access');
    $('#cat_addbiblio #tab8XX_panel h3').append(' - Series added entry and electronic access');
    $('#cat_addbiblio .toolbar-tabs-container a[href="#tab9XX_panel"]').append('<br>Koha related');
    $('#cat_addbiblio #tab9XX_panel h3').append(' - Koha related');
~~~

---

## Append vs After

.append() vs .after()

.append() puts data inside of the selected element at the end of the element

.after() puts data after the selected element

---

### .append()

~~~javascript
//Add link to Koha community website to all pages
  $('#sub-header').append('<div><h3 align="center"><a href="https://koha-community.org/" target="_blank">Koha community website</a></h3></div>');

~~~

### .after()

~~~javascript
//Add link to Koha community website to all pages
  $('#sub-header').after('<div><h3 align="center"><a href="https://koha-community.org/" target="_blank">Koha community website</a></h3></div>');
~~~

## More complex stuff

### .click() function

~~~javascript
//Home > Reports > Guided reports wizard > Saved reports
//(/cgi-bin/koha/reports/guided_reports.pl?op=list)
  //BEGIN Make action button drop-up options on that button open report in new tab 
    $('#rep_guided_reports_start .btn-group.dropup').click(function () {
      $('.dropdown-menu a, .btn-xs').attr('target', '_blank');
    });
~~~

### Embiggen the notes area in reports:

~~~javascript
//Home > Reports > Guided reports wizard > Saved reports > GHW - Items with important fields that are blank or have problematic values (214) > Edit
//(/cgi-bin/koha/reports/guided_reports.pl?id=214&op=edit_form)
  //Makes notes field full height 
    $("#rep_guided_reports_start #notes").attr('class', 'sqlnotes'); 
    $('.sqlnotes').one('click', function() { 
      $('.sqlnotes').css({'height': 'auto', 'width': '85%', 'overflow-y': 'hidden;'}); 
      $('.sqlnotes').height(this.scrollHeight).width(this.scrollWidth);
    });
~~~ 

## File bugs

If you’re using jQuery or Javascript to work around a problem, file a bug


## Ask the community for help:

- Koha community mailing list

  - https://koha-community.org/support/koha-mailing-lists/
  
- koha-US

  - https://koha-us.org/mailing-lists/

- Mattermost server

  - https://chat.koha-community.org/l
  - (It's like Slack but better)

## My contact information

George Williams

- Next Search Catalog Coordinator at Northeast Kansas Library System
- (see https://nextkansas.org/)
- gwilliams@nekls.org
- @georgehwilliams (on MatterMost)
- Has used Koha for 14+ years