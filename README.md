Download Link: https://assignmentchef.com/product/solved-web422-assignment-2
<br>
To work with our “Sales” API (from Assignment 1) on the client-side to produce a rich user interface for accessing data.  We will practice using well-known CSS/JS code and libraries including Lodash, Moment.js, jQuery &amp; Bootstrap

Sample Solution:

You can see a video of the solution running at the link below:




<a href="https://ict.senecacollege.ca/~patrick.crawford/shared/summer-2020/web422/A2/A2.mp4">https://ict.senecacollege.ca/~patrick.crawford/shared/summer</a><a href="https://ict.senecacollege.ca/~patrick.crawford/shared/summer-2020/web422/A2/A2.mp4">–</a><a href="https://ict.senecacollege.ca/~patrick.crawford/shared/summer-2020/web422/A2/A2.mp4">2020/web422/A2/A2.mp4</a> Specification:

For this assignment, we will create a single table that shows a subset of the sale data (ie: columns: <strong>Customer, Store Location, Number of Items and Sale Date</strong>). When the user clicks on a specific sale (row) in the table, they will be shown a modal window that contains additional detail about the sale.  We will be making use of the Bootstrap framework to render our HTML, jQuery to work with the DOM and Lodash / Moment.js to format the data.




<h1>The Solution Directory</h1>

The first step is to create a new directory for your solution, open it in Visual Studio Code and add following folders / files:




We will not be including any of the JavaScript / CSS libraries locally.  Instead, we will be leveraging their CDN locations (See the <a href="https://web422.ca/notes/week02">Week 2 notes</a> for the &lt;script&gt; and &lt;link&gt; elements necessary to include jQuery, Bootstrap, Lodash and Moment).  <strong>Note:</strong> Remember that the order is important, ie: jQuery should be included <em>before</em> the Bootstrap JavaScript and your main.js file should be included last.




Creating the Static HTML:

Next, we must create some Static HTML as a framework for the dynamic content.

Open your index.html file and add the minimum code required for an HTML5 page (HINT: type <strong>!</strong> and then immediately type the <strong>tab </strong>key to get an HTML 5 skeleton).  Once this is complete, include links for:

<ul>

 <li>The Bootstrap 3.4.1 Minified CSS File (Using the CDN)</li>

 <li>Your <strong>css</strong> file (<strong>NOTE</strong>: This file will only consist of a single selector (for now) to ensure that your “sale-table” (or whatever you wish to call it causes the cursor to change to a “pointer” whenever a user moves their mouse over a row), ie: #sale-table <strong>tr</strong>:hover{ <strong>cursor</strong>:<strong>pointer</strong>; }</li>

 <li>The jQuery 3.4.1 Slim, Minified JS File (Using the CDN)</li>

 <li>The Bootstrap 3.4.1 Minified JS File (Using the CDN)</li>

 <li>The Lodash 4.17.5 Minified JS File (Using the CDN)</li>

 <li>The Moment (With Locales) 2.24.0 Minified JS File (Using the CDN)</li>

 <li>Your <strong>js</strong> file</li>

</ul>

With all of our libraries and files in place, we can concentrate on placing the static HTML content on the page.  This includes the following:




<h2>Navbar</h2>

Assignment 2 will use an extremely simplified Bootstrap 3 navbar.  Begin by copying the full <strong>Default Navbar</strong> example HTML code from the official documentation: <a href="https://getbootstrap.com/docs/3.4/components/#navbar-default">https://getbootstrap.com/docs/3.4/components/#navbar</a><a href="https://getbootstrap.com/docs/3.4/components/#navbar-default">–</a><a href="https://getbootstrap.com/docs/3.4/components/#navbar-default">default</a> and pasting it as the first element within the &lt;body&gt; of your file.

<ul>

 <li>Next, proceed to remove <strong>all</strong> <strong>child elements</strong> from the “bs-example-navbar-collapse-1” &lt;div&gt; element</li>

 <li>In the (now empty) “bs-example-navbar-collapse-1” &lt;div&gt; element, put back a single navigation item and label it “Sales”, ie:</li>

</ul>

<strong>&lt;ul</strong> class=”nav navbar-nav”<strong>&gt;</strong>

<strong>    &lt;li</strong> class=”active”<strong>&gt;&lt;a</strong> href=”#”<strong>&gt;</strong>Sales<strong>&lt;span</strong> class=”sr-only”<strong>&gt;</strong>(current)<strong>&lt;/span&gt;&lt;/a&gt;&lt;/li&gt; &lt;/ul&gt;</strong>

<ul>

 <li>Finally, change the “navbar-brand” to be your name</li>

</ul>

When completed, your navbar should look like the following







<h2>Bootstrap Grid System (1 Column)</h2>

Since we are leveraging Bootstrap for this assignment, we should make use of their excellent responsive grid system.  Beneath the navbar, add the following HTML

<ul>

 <li>Include a &lt;div&gt; element with the class “container” (so that our content is centered)</li>

 <li>Within the “container”, create a &lt;div&gt; with class “row”</li>

 <li>Within the “row”, create a &lt;div&gt; with class “col-md-12” (we will only have one column to show our data)</li>

</ul>




<h2>Main Table Skeleton</h2>

The main interface that users will interact with to view data in our application is a HTML table consisting of <strong>4 columns:</strong> <strong>Customer, Store Location, Number of Items </strong>and <strong>Sale Date</strong>.  Create this table within your “col-md-12” container according to the following specification:

<ul>

 <li>The &lt;table&gt; element should have the class “table” and a unique id, ie: “sale-table”, since we will be accessing it programmatically from JavaScript</li>

 <li>The &lt;thead&gt; element should contain one row</li>

 <li>The single header row should have 4 table heading elements with the text:</li>

</ul>

o Customer o Store Loation o Number of Items o Sale Date

<ul>

 <li>The &lt;tbody&gt; element should be empty</li>

</ul>

Once your table is in place, your app should look like the following:










<h2>Paging Control</h2>

Since our “sales” collection contains approximately 5000 documents (more or less if you modified the data during your testing of Assignment 1), we will leverage our Web API’s pagination feature when pulling sales from the database (ie: <strong>/api/sales?page=1&amp;perPage=10</strong>, etc).  To give the user some control over which page they wish to see, we must include a primitive pagination control (for this assignment, we will not let them “jump” to a specific page, but instead we will let them go back and forth between the pages in sequence).  To accomplish this, we must place the pagination buttons on our page before wiring up their functionality using jQuery:

<ul>

 <li>Begin by copying the full <strong>Pagination</strong> HTML code from the official documentation:</li>

</ul>

<a href="https://getbootstrap.com/docs/3.4/components/#pagination">https://getbootstrap.com/docs/3.4/components/#pagination</a> and pasting it directly underneath your newly created “sale-table”.

<ul>

 <li>Next, delete the list items that contain the numbers <strong>2</strong>, <strong>3</strong>, <strong>4</strong> and <strong>5</strong> (leaving just <strong>1</strong>)</li>

 <li>Give each of the 3 remaining &lt;a&gt; elements (nested within the &lt;li&gt; elements) unique id values such as “previous-page”, “current-page” and “next-page” (we will use these id values to add functionality to the links and display the current page)</li>

 <li>Finally, remove the text <strong>1</strong> from the middle link (it will be added dynamically later).</li>

</ul>

Once your pagination control is in place, your app skeleton should look like the following:







<h2>“Generic” Modal Window Container</h2>

We will be showing all of our detailed Sale information in a Bootstrap modal window.  Since every time we show the modal window, it will have different content (Specific to the Sale that was clicked), we must add an empty, <strong>generic</strong> modal window to the bottom of our page.

To get the correct HTML to use for your Bootstrap modal window, use <a href="https://getbootstrap.com/docs/3.4/javascript/#modals-examples">the following example</a> from the documentation as a starting point.

Once you have copied and pasted the “modal” HTML into the bottom of your index.html page (ie, before all of your &lt;script&gt;&lt;/script&gt; tags), make the following changes:

<ul>

 <li>Give your &lt;div&gt; with the class “<strong>modal fade</strong>” a unique <strong>id</strong>, ie: “<strong>sale-modal</strong>“. We will need to reference this element every time we wish to show a <strong>modal window.</strong></li>

 <li>Remove the “Modal Title” text from the &lt;h4&gt; element with class “<strong>modal-title</strong>“. We will be using jQuery to populate this with the selected Sale <strong>_id</strong></li>

 <li>Remove the &lt;p&gt; element with the text “One fine body…” from the &lt;div&gt; element with class “<strong>modalbody</strong>“. We will be using jQuery to populate this with the detailed Sale information such as customer information and products purchased.</li>

 <li>Finally, remove the button element with the text “Save Changes”. This modal is used to display information only, so a “save” button is not required.</li>

</ul>




JavaScript File (main.js):

Now that we have all of our static HTML / CSS in place, we can start dynamically adding content and responding to user events using JavaScript.  In your <strong>main.js</strong> file add the following variables &amp; function at the top of the file:

<ul>

 <li><strong>saleData</strong> (array)</li>

</ul>

This should be an empty array (we will populate it later with a “fetch” call to our back end API) • <strong>page </strong>(number)

This will keep track of the current page that the user is viewing.  Set it to <strong>1</strong> as the default value

<ul>

 <li><strong>perPage </strong>(number)</li>

</ul>

This will be a constant value that we will use to reference how many sale items we wish to view on each page of our application.  For this assignment, we will set it to <strong>10</strong>.

<ul>

 <li><strong>saleTableTemplate </strong>(Lodash template)</li>

</ul>

This will be a constant value that consists solely of a Lodash template (defined using the _.template() function).

The idea for this template is that it will provide the functionality to return all the rows for our main “sale-table”, given an array of “sale” data.  For example, if the <strong>saleTableTemplate</strong> was invoked with the first two results back from our <strong>Web API</strong> (<strong><em>left</em></strong>), we it should output the following <strong>HTML</strong> (<strong><em>right</em></strong>):




<strong>&lt;tr</strong> data-id=”5bd761deae323e45a93cdcb3″<strong>&gt;</strong>

<strong>    &lt;td&gt;</strong><a href="/cdn-cgi/l/email-protection" class="__cf_email__" data-cfemail="8af9e5e7e2e3f9cae1eff8efe0a4e8ed">[email protected]</a><strong>&lt;/td&gt;</strong>

<strong>    &lt;td&gt;</strong>Austin<strong>&lt;/td&gt;</strong>

<strong>    &lt;td&gt;</strong>4<strong>&lt;/td&gt;</strong>

<strong>    &lt;td&gt;</strong>Sunday, December 31, 2017 1:15 PM<strong>&lt;/td&gt;</strong>

<strong>&lt;/tr&gt;</strong>

<strong>&lt;tr</strong> data-id=”5bd761deae323e45a93cdd61″<strong>&gt;</strong>

<strong>    &lt;td&gt;</strong><a href="/cdn-cgi/l/email-protection" class="__cf_email__" data-cfemail="7b121512010e010e103b1e16551c1a">[email protected]</a><strong>&lt;/td&gt;</strong>

<strong>    &lt;td&gt;</strong>Seattle<strong>&lt;/td&gt;</strong>

<strong>    &lt;td&gt;</strong>7<strong>&lt;/td&gt;</strong>

<strong>    &lt;td&gt;</strong>Sunday, December 31, 2017 11:11 AM<strong>&lt;/td&gt; &lt;/tr&gt;</strong>




You will notice a few things about the formatting of each row in the returned result, specifically:

<ul>

 <li>The template loops through each object in the array to produce a &lt;tr&gt; element (<strong>HINT</strong>: _.forEach() can be used here)</li>

 <li>Each &lt;tr&gt; has a “data-id” attribute that matches the <strong>_id</strong> property of the object in the current iteration</li>

 <li>The first &lt;td&gt; content contains the <strong>email</strong> property of the object in the current iteration</li>

 <li>The second &lt;td&gt; content contains the <strong>storeLocation</strong> property of the object in the current iteration</li>

 <li>The third &lt;td&gt; content contains the <strong>number of elements</strong> in the <strong>items</strong> property of the object in the current iteration</li>

 <li>The final &lt;td&gt; content contains a formatted date using the <strong>saleDate</strong> property of the object in the current iteration. <strong>HINT:</strong> To achieve this, the following “moment” formatting code may be used within the template: <strong>utc(</strong><em>some UTC date string here</em><strong>).local().format(</strong><strong>‘LLLL’) </strong></li>

 <li><strong>HINT: Place all the HTML / Code for your template within a string defined using ` `</strong> (this will allow you to write our template string across multiple lines.</li>

</ul>

<strong> </strong>

<ul>

 <li><strong>saleModelBodyTemplate </strong>(Lodash template)</li>

</ul>

This template is slightly more complicated than the previous <strong>saleTableTemplate.  </strong>This template must provide all of the layout and formatting for the content contained within our modal window for a specific “sale”.  For example, if the <strong>saleModelBodyTemplate</strong> was invoked with the first result back from our <strong>Web API</strong> (<strong><em>left</em></strong>), we it




should output the following <strong>HTML</strong> (<strong><em>right</em></strong>):

<strong> </strong>

<strong> </strong>

<strong>&lt;h4&gt;</strong>Customer<strong>&lt;/h4&gt;</strong>

<strong>&lt;strong&gt;</strong>email:<strong>&lt;/strong&gt;</strong> <a href="/cdn-cgi/l/email-protection" class="__cf_email__" data-cfemail="34475b595c5d47745f5146515e1a5653">[email protected]</a><strong>&lt;br&gt;</strong>

<strong>&lt;strong&gt;</strong>age:<strong>&lt;/strong&gt;</strong> 33<strong>&lt;br&gt;</strong>

<strong>&lt;strong&gt;</strong>satisfaction:<strong>&lt;/strong&gt;</strong> 1 / 5

<strong>&lt;br&gt;&lt;br&gt;</strong>

<strong>&lt;h4&gt;</strong> Items: $213.66 <strong>&lt;/h4&gt;</strong>

<strong>&lt;table</strong> class=”table”<strong>&gt;</strong>

<strong>&lt;thead&gt;</strong>

<strong>&lt;tr&gt;</strong>

<strong>&lt;th&gt;</strong>Product Name<strong>&lt;/th&gt;</strong>

<strong>&lt;th&gt;</strong>Quantity<strong>&lt;/th&gt;</strong>

<strong>&lt;th&gt;</strong>Price<strong>&lt;/th&gt;</strong>

<strong>&lt;/tr&gt;</strong>

<strong>&lt;/thead&gt;</strong>

<strong>&lt;tbody&gt;</strong>

<strong>&lt;tr&gt;</strong>

<strong>&lt;td&gt;</strong>pens<strong>&lt;/td&gt;</strong>

<strong>&lt;td&gt;</strong>4<strong>&lt;/td&gt;</strong>

<strong>&lt;td&gt;</strong>$25.32<strong>&lt;/td&gt;</strong>

<strong>&lt;/tr&gt;</strong>

<strong>&lt;tr&gt;</strong>

<strong>&lt;td&gt;</strong>notepad<strong>&lt;/td&gt;</strong>

<strong>&lt;td&gt;</strong>1<strong>&lt;/td&gt;</strong>

<strong>&lt;td&gt;</strong>$30.05<strong>&lt;/td&gt;</strong>

<strong>&lt;/tr&gt;</strong>

<strong>&lt;tr&gt;</strong>

<strong>&lt;td&gt;</strong>binder<strong>&lt;/td&gt;</strong>

<strong>&lt;td&gt;</strong>1<strong>&lt;/td&gt;</strong>

<strong>&lt;td&gt;</strong>$17.01<strong>&lt;/td&gt;</strong>

<strong>&lt;/tr&gt;</strong>

<strong>&lt;tr&gt;</strong>

<strong>&lt;td&gt;</strong>pens<strong>&lt;/td&gt;</strong>

<strong>&lt;td&gt;</strong>4<strong>&lt;/td&gt;</strong>

<strong>&lt;td&gt;</strong>$16.33<strong>&lt;/td&gt;</strong>

<strong>&lt;/tr&gt;</strong>

<strong>&lt;/tbody&gt;</strong>

<strong>&lt;/table&gt;</strong>

<strong> </strong>




Once again, you should notice a few things about the expected output, specifically:

<ul>

 <li>The output begins with a static &lt;h4&gt; Element with the text “Customer”</li>

 <li>The customer’s <strong>email</strong>, <strong>age</strong> and <strong>satisfaction</strong> values are rendered next to a corresponding label contained within the element &lt;strong&gt;&lt;/strong&gt;. Specifically, the <strong>satisfaction</strong> value is followed with the text  “/ 5” to indicate to the user that this rating is indeed out of 5 and not out of 10 or 100.</li>

 <li>We have two &lt;br&gt; elements for spacing (feel free to use CSS here instead)</li>

 <li>The text “Items” contained within the &lt;h4&gt; element is followed by a “$” character and a total price value. This value must be calculated beforehand (see the functionality below) and added to a new property of the object called <strong>total</strong>.  In order to format it to 2 decimal points, the following code can be used within the template: <em>some sale total property here</em>.toFixed(2)</li>

 <li>A &lt;table&gt; element with class=”table” must be added with the header row containing the text “<strong>Product Name</strong>“, “<strong>Quantity</strong>” and “<strong>Price</strong>“, and each row (&lt;tr&gt;) of the table body must show data for an item purchased (from the “items” array) and have three columns (&lt;td&gt;), each containing information about the item, specifically:</li>

 <li>name</li>

 <li>quantity</li>

 <li>price</li>

</ul>

<strong>Hint</strong>: <strong>Place all the HTML / Code for your template within a string defined using ` `</strong> (this will allow you to write our template string across multiple lines.  Also, get the first part working first (ie: email, age and satisfaction, etc).  Once this works, then worry about adding the table and the _.forEach() for the rows.




<ul>

 <li><strong>function loadSaleData</strong>()</li>

</ul>

Now that our templates and global variables are in place, we can write a utility function to actually <strong>populate</strong> the <strong>saleData</strong> array with data from our API created in Assignment 1 (now sitting on Heroku).  To achieve this, the loadSaleData function must:




<ul>

 <li>make a “fetch” request to our Web API hosted on Heroku using the route:</li>

</ul>

/api/sales?page=<strong><em>page</em></strong>&amp;perPage=<strong><em>perPage</em></strong>

Here, the values of <strong>page</strong> and <strong>perPage </strong>must be the values of the variables: <strong>page</strong> and <strong>perPage </strong>that you declared at the top of the file at the beginning of this assignment – <strong>perPage</strong> is a constant value and <strong>page</strong> is the current working page.

<ul>

 <li>When the fetch request has returned and the json data has been parsed:

  <ul>

   <li>set the global <strong>saleData</strong> array to be the data returned from the request</li>

   <li>invoke the <strong>saleTableTemplate</strong> with the data returned from the request (ie:</li>

  </ul></li>

</ul>

<strong>saleTableTemplate({sales: data})</strong>) and store the return value in a variable.

<ul>

 <li>Select the &lt;tbody&gt; element of your main “sale-table” and set its html (.html()) to be the returned value from when you invoked the <strong>saleTableTemplate</strong> function, above.</li>

 <li>Select the <strong>current-page</strong> element (from your pagination control) and set its html (.html()) to be the value of the current <strong>page</strong></li>

</ul>




Now that our loadSaleData utility function as well as our templates and global variables are in place, let’s add the following code to be executed when the document is <strong><em>ready</em></strong> (ie: within the <strong>$(function(){</strong> … <strong>});</strong> callback ),

<ul>

 <li>The first thing that needs to be done, is to invoke the <strong>loadSaleData()</strong> function to populate our table with data and set the current working page</li>

 <li>Next, we must wire up <strong>click</strong> events for all <strong>&lt;tr&gt; </strong>elements contained within the <strong>&lt;tbody&gt;</strong> of our main “sale-table” (HINT: This can be done by selecting the correct element and using the “.on()” method).</li>

</ul>

The purpose of this event is to show a more detailed view of the sale to the user in a Bootstrap modal window (ie: our “Generic” Modal Window Container).  To accomplish this, a number of things need to happen:




<ul>

 <li>We must store the “id” of the clicked row in a local variable (ie: <em>clickedId</em>). This value can be obtained by using the jQuery code: $(<strong>this</strong>).attr(“data-id”); since the id of every sale is saved as the value of a “dataid” attribute on each &lt;tr&gt; element in the “sale-table”.</li>

 <li>Next, we must use this <em>clickedId</em> value to find the matching sale document within the “saleData” array, so that we can read the detailed sale information from the object. This process can be done in many ways, however the Lodash library provides a handy function that we can use: <a href="https://lodash.com/docs/4.17.15#find">find()</a> (or, alternatively, you can try the <a href="https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array/find">ES6 find() method</a><a href="https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array/find">)</a>. Using this method, we can find the object in “saleData” that has an <strong>_id</strong> property value that matches our <em>clickedId</em>!</li>

</ul>

Lastly, take this object and store it in a separate variable (ie: clickedSale).

<ul>

 <li>Next, we must assign a new property to our “clickedSale” called “total”. This property will contain the total cost of all items in the sale.  To calculate this value, we can loop through the “items” array in the “clickedSale” and add up the cost of all items using the formula <strong>total += (price * quantity)</strong> for every item.  Having the “total” in place for the “clickedSale” will provide data for that “items” value in the &lt;h4&gt; of our modal window</li>

 <li>Once this is done, set the HTML for the <strong>modal-title</strong> of the “sale-modal” to read “Sale: <strong>_id</strong>” where <strong>_id</strong> is the _id value of the “clickedSale”</li>

 <li>Next, invoke the <strong>saleModalBodyTemplate()</strong> function with the value of the “clickedSale” to obtain the full HTML code (as outlined above). Take this HTML and add it as the content of the <strong>modal-body</strong> of the “sale-modal”.</li>

 <li>Finally, show the modal by selecting it using jQuery and invoking the <strong>.modal()</strong> function such that the user cannot dismiss the modal by hitting “esc” on the keyboard, or clicking on the modal “backdrop”.</li>

 <li>With our modal window code all working nicely, the last thing that must be done is to wire up both of the “pagination” buttons such that the use can move back and forth between the pages in the application. To accomplish this:</li>

 <li>Wire up a <strong>click</strong> event for the “previous-page” button (HINT: This can be done by selecting the correct element and using the “.on()” method).</li>

</ul>




Once this button has been clicked, we have to simply:

<ul>

 <li><strong>decrease</strong> the value of our global <strong>page</strong> variable by 1, only if its current value is greater than 1 (ie: we do not want to let users access page values lower than 1)</li>

 <li>invoke the <strong>loadSaleData()</strong> function again, to refresh the “sale-table”</li>

</ul>




<ul>

 <li>Wire up a <strong>click</strong> event for the “next-page” button (HINT: This can be done by selecting the correct element and using the “.on()” method).</li>

</ul>




Once this button has been clicked, we have to simply:

<ul>

 <li><strong>increase</strong> the value of our global <strong>page</strong> variable by 1</li>

 <li>invoke the <strong>loadSaleData()</strong> function again, to refresh the “sale-table”</li>

</ul>