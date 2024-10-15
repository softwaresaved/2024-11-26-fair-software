---
layout: workshop      # DON'T CHANGE THIS.
# More detailed instructions (including how to fill these variables for an
# online workshop) are available at
# https://carpentries.github.io/workshop-template/customization/index.html
venue: ""        # brief name of the institution that hosts the workshop without address (e.g., "Euphoric State University")
address: "online"      # full street address of workshop (e.g., "Room A, 123 Forth Street, Blimingen, Euphoria"), videoconferencing URL, or 'online'
country: "gb"      # lowercase two-letter ISO country code such as "fr" (see https://en.wikipedia.org/wiki/ISO_3166-1#Current_codes) for the institution that hosts the workshop
language: "en"     # lowercase two-letter ISO language code such as "fr" (see https://en.wikipedia.org/wiki/List_of_ISO_639-1_codes) for the workshop
latitude: "45"        # decimal latitude of workshop venue (use https://www.latlong.net/)
longitude: "-1"       # decimal longitude of the workshop venue (use https://www.latlong.net)
humandate: "26 - 29 November 2024"    # human-readable dates for the workshop (e.g., "Feb 17-18, 2020")
humantime: "9:00 - 13:00 GMT (UTC + 0)"    # human-readable times for the workshop e.g., "9:00 am - 4:30 pm CEST (7:00 am - 2:30 pm UTC)"
startdate: 2024-07-01      # machine-readable start date for the workshop in YYYY-MM-DD format like 2015-01-01
enddate: 2024-07-04        # machine-readable end date for the workshop in YYYY-MM-DD format like 2015-01-02
instructor: ["Kamilla Kopec-Harding", "Sam Mangham", "Colin Sauze"] # boxed, comma-separated list of instructors' names as strings, like ["Kay McNulty", "Betty Jennings", "Betty Snyder"]
helper: "Philly Broadbent"     # boxed, comma-separated list of helpers' names, like ["Marlyn Wescoff", "Fran Bilas", "Ruth Lichterman"]
email: ["a.nenadic@software.ac.uk"]    # boxed, comma-separated list of contact email addresses for the host, lead instructor, or whoever else is handling questions, like ["marlyn.wescoff@example.org", "fran.bilas@example.org", "ruth.lichterman@example.org"]
collaborative_notes:  # optional: URL for the workshop collaborative notes, e.g. an Etherpad or Google Docs document (e.g., https://pad.carpentries.org/2015-01-01-euphoria)
eventbrite:           # optional: alphanumeric key for Eventbrite registration, e.g., "1234567890AB" (if Eventbrite is being used)
---

{% comment %}
EVENTBRITE

This block includes the Eventbrite registration widget if
'eventbrite' has been set in the header.  You can delete it if you
are not using Eventbrite, or leave it in, since it will not be
displayed if the 'eventbrite' field in the header is not set.
{% endcomment %}
{% if page.eventbrite %}
<strong>Some adblockers block the registration window. If you do not see the
  registration box below, please check your adblocker settings.</strong>
<iframe
  src="https://www.eventbrite.com/tickets-external?eid={{page.eventbrite}}&ref=etckt"
  frameborder="0"
  width="100%"
  height="280px"
  scrolling="auto">
</iframe>
{% endif %}


<h2 id="general">General Information</h2>

This workshop is organised by the Software Sustainability Institute.

{% if site.pilot %}
This is a pilot workshop, testing out a lesson that is still under development. The lesson authors would appreciate any feedback you can give them about the lesson content and suggestions for how it could be further improved.
{% endif %}

<p id="material">
  <strong>Course material:</strong>
  <a href="https://carpentries-incubator.github.io/fair-research-software/" target="blank">Course material</a> that will be used at the workshop is available online.
</p>

{% comment %}
LOCATION

This block displays the address and links to maps showing directions
if the latitude and longitude of the workshop have been set.  You
can use https://www.latlong.net/ to find the lat/long of an
address.
{% endcomment %}
{% assign begin_address = page.address | slice: 0, 4 | downcase  %}
{% if page.address == "online" %}
{% assign online = "true_private" %}
{% elsif begin_address contains "http" %}
{% assign online = "true_public" %}
{% else %}
{% assign online = "false" %}
{% endif %}
{% if page.latitude and page.longitude and online == "false" %}
<p id="where">
  <strong>Where:</strong>
  {{page.address}}.
  Get directions with
  <a href="//www.openstreetmap.org/?mlat={{page.latitude}}&mlon={{page.longitude}}&zoom=16">OpenStreetMap</a>
  or
  <a href="//maps.google.com/maps?q={{page.latitude}},{{page.longitude}}">Google Maps</a>.
</p>
{% elsif online == "true_public" %}
<p id="where">
  <strong>Where:</strong>
  online at <a href="{{page.address}}">{{page.address}}</a>.
  If you need a password or other information to access the training,
  the instructor will pass it on to you before the workshop.
</p>
{% elsif online == "true_private" %}
<p id="where">
  <strong>Where:</strong> This workshop will take place online via Zoom - 
  the organisers will provide registered participants with the connection information closer to the workshop.
</p>
{% endif %}

{% comment %}
DATE

This block displays the date and links to Google Calendar.
{% endcomment %}
{% if page.humandate %}
<p id="when">
  <strong>When:</strong>
  {{page.humandate}}, {{page.humantime}}.
</p>
{% endif %}

{% comment %}
SPECIAL REQUIREMENTS

Modify the block below if there are any special requirements.
{% endcomment %}
<p id="requirements">
  <strong>Requirements:</strong>
  {% if online == "false" %}
    Participants must bring a laptop with a
    Mac, Linux, or Windows operating system (not a tablet, Chromebook, etc.) that they have administrative privileges on.
  {% else %}
    Participants must have access to a computer with a
    Mac, Linux, or Windows operating system (not a tablet, Chromebook, etc.) that they have administrative privileges on.
  {% endif %}
  Participants should have a few specific software packages installed - please make sure to follow the <a href="#setup">setup instructions</a>.
</p>

{% comment %}
CONTACT EMAIL ADDRESS

Display the contact email address set in the configuration file.
{% endcomment %}
<p id="contact">
  <strong>Contact:</strong>
  Please email
  {% if page.email %}
  {% for email in page.email %}
  {% if forloop.last and page.email.size > 1 %}
  or
  {% else %}
  {% unless forloop.first %}
  ,
  {% endunless %}
  {% endif %}
  <a href='mailto:{{email}}'>{{email}}</a>
  {% endfor %}
  {% else %}
  to-be-announced
  {% endif %}
  for more information.
</p>

{% comment %}
WHO CAN ATTEND?

If you would like to specify who can attend the workshop,
you can use the section below.

Move the 'endcomment' tag above the beginning of the following
<p> tag to make this section visible.

Edit the text to match who can attend the workshop. For instance:
- This workshop is open to affiliates to ABC university.
- This workshop is open to the public.
- If you are interested in attending this workshop, contact me@example.com
  for more information

<p id="who-can-attend">
    <strong>Who can attend?:</strong>
    This workshop is open to ....
</p>
{% endcomment %}

<hr/>

{% comment%}
CODE OF CONDUCT
{% endcomment %}
<h2 id="code-of-conduct">Code of Conduct</h2>

<p>
Everyone who participates in this workshop is required to conform to the <a href="https://docs.carpentries.org/topic_folders/policies/code-of-conduct.html">Code of Conduct</a>.
</p>

{% comment %}
<p class="text-center">
  <a href="https://goo.gl/forms/KoUfO53Za3apOuOK2">
    <button type="button" class="btn btn-info">Report a Code of Conduct Incident</button>
  </a>
</p>
{% endcomment %}

<hr/>


{% comment %}
Collaborative Notes

If you want to use an Etherpad, go to

https://pad.carpentries.org/YYYY-MM-DD-site

where 'YYYY-MM-DD-site' is the identifier for your workshop,
e.g., '2015-06-10-esu'.

Note we also have a CodiMD (the open-source version of HackMD)
available at https://codimd.carpentries.org
{% endcomment %}
{% if page.collaborative_notes %}
<h2 id="collaborative_notes">Collaborative Notes</h2>

<p>
We will use this <a href="{{ page.collaborative_notes }}">collaborative document</a> for chatting, taking notes, and sharing URLs and bits of code.
</p>
<hr/>
{% endif %}


{% comment %}
SURVEYS - DO NOT EDIT SURVEY LINKS
{% endcomment %}
<h2 id="surveys">Surveys</h2>
<p>Please be sure to complete these surveys before and after the workshop.</p>
<p><a href="https://docs.google.com/forms/d/e/1FAIpQLSc7tBaQSjy3W5LZSHFMWgGE1Ynw38jGAgdpDamqkiTTv1qL2w/viewform">Pre-workshop Survey</a></p>
<p><a href="https://docs.google.com/forms/d/e/1FAIpQLSdPv3BZYMlRIyP5DgWdOuLSwCnLdrd8CiONCRxKIVMgwPY33g/viewform">Post-workshop Survey</a></p>

<hr/>


{% comment %}
SCHEDULE

Show the workshop's schedule.

Small changes to the schedule can be made by modifying the
`schedule.html` found in the `_includes` folder for your
workshop type (`swc`, `lc`, or `dc`). Edit the items and
times in the table to match your plans. You may also want to
change 'Day 1' and 'Day 2' to be actual dates or days of the
week.

For larger changes, a blank template for a 4-day workshop
(useful for online teaching for instance) can be found in
`_includes/custom-schedule.html`. Add the times, and what
you will be teaching to this file. You may also want to add
rows to the table if you wish to break down the schedule
further. To use this custom schedule here, replace the block
of code below the Schedule `<h2>` header below with
`{% include custom-schedule.html %}`.
{% endcomment %}

<h2 id="schedule">Schedule</h2>
<div class="row">
  <div class="col-md-6">
    <h3>Day 1, 26 November 2024, 9:00 - 13:00 UTC </h3>
    <table class="table table-striped">
      <tr> <td>09:00</td>  <td>Course introduction</td> </tr>
      <tr> <td>09:30</td>  <td>FAIR reseach software</td> </tr>
      <tr> <td>10:00</td>  <td>Break</td> </tr>
      <tr> <td>11:15</td>  <td>Tools and practices for FAIR research software development</td> </tr>
      <tr> <td>12:15</td>  <td>Break</td> </tr>
      <tr> <td>12:30</td>  <td>Tools and practices for FAIR research software development (cont'd)</td> </tr>
      <tr> <td>13:00</td>  <td>End</td> </tr>
    </table>
  </div>
  <div class="col-md-6">
    <h3>Day 2, 27 November 2024, 9:00 - 13:00 UTC</h3>
    <table class="table table-striped">
      <tr> <td>09:00</td>  <td>Day 1 recap</td> </tr>
      <tr> <td>09:15</td>  <td>Version control</td> </tr>
      <tr> <td>10:00</td>  <td>Break</td> </tr>
      <tr> <td>10:15</td>  <td>Version Control (cont'd)</td> </tr>
      <tr> <td>11:15</td>  <td>Break</td> </tr>
      <tr> <td>11:30</td>  <td>Code readability</td> </tr>
      <tr> <td>13:00</td>  <td>End</td> </tr>
    </table>
  </div>
    <div class="col-md-6">
    <h3>Day 3, 28 November 2024, 9:00 - 13:00 UTC</h3>
    <table class="table table-striped">
      <tr> <td>09:00</td>  <td>Day 2 recap</td> </tr>
      <tr> <td>09:15</td>  <td>Code testing</td> </tr>
      <tr> <td>10:00</td>  <td>Break</td> </tr>
      <tr> <td>10:15</td>  <td>Code testing (cont'd)</td> </tr>
      <tr> <td>11:15</td>  <td>Break</td> </tr>
      <tr> <td>11:30</td>  <td>Documenting code</td> </tr>
      <tr> <td>13:00</td>  <td>End</td> </tr>
    </table>
  </div>
    <div class="col-md-6">
    <h3>Day 4, 29 November 2024, 9:00 - 13:00 UTC</h3>
    <table class="table table-striped">
      <tr> <td>09:00</td>  <td>Day 3 recap</td> </tr>
      <tr> <td>09:15</td>  <td>Documenting code (cont'd)</td> </tr>
      <tr> <td>10:00</td>  <td>Break</td> </tr>
      <tr> <td>10:15</td>  <td>Open project collaboration & management</td> </tr>
      <tr> <td>11:15</td>  <td>Break</td> </tr>
      <tr> <td>11:30</td>  <td>Open project collaboration & management (cont'd)</td> </tr>
      <tr> <td>13:00</td>  <td>Wrap-up/End</td> </tr>
    </table>
  </div>
</div>

<hr/>


{% comment %}
SETUP

Delete irrelevant sections from the setup instructions.  Each
section is inside a 'div' without any classes to make the beginning
and end easier to find.

This is the other place where people frequently make mistakes, so
please preview your site before committing, and make sure to run
'tools/check' as well.
{% endcomment %}

<h2 id="setup">Setup</h2>

<p>
  Please make sure that you have all the <a target="_blank" href="https://carpentries-incubator.github.io/fair-research-software/#setup">required software</a> installed
  before coming to the workshop. If you are having installation or setup problems - please <a href="#contact">contact the workshop organisers</a> who will be able to assist you. Failing to have a working setup on your machine will slow everyone down at the workshop. 
</p>

