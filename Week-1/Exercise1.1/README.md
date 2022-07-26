
When a user enters an URL in the browser, how does the browser fetch the desired result ?

What is a URL?

URL stands for Uniform Resource Locator. A URL is nothing more than the address of a given unique resource on the Web where we want to go to interact with or find information.
In theory, each valid URL points to a unique resource. Such resources can be an HTML page, a CSS document, an image, etc.

Parts of URL:

Let’s take an example:
![url-all](https://user-images.githubusercontent.com/64431648/181002547-91131d35-6dd4-43fa-9377-5dbd7c44d351.png)


Scheme

![scheme](https://user-images.githubusercontent.com/64431648/181002622-c5f82259-a8b9-443f-af94-e0a078177714.png)

The first part of the URL is the scheme, which indicates the protocol that the browser must use to request the resource (a protocol is a set method for exchanging or transferring data around a computer network). Usually for websites the protocol is HTTPS or HTTP (its unsecured version). Addressing web pages requires one of these two, but browsers also know how to handle other schemes such as mailto: (to open a mail client), so don't be surprised if you see other protocols.


Authority

![authority](https://user-images.githubusercontent.com/64431648/181002657-d072dedb-a427-4c16-aded-0cab1b378d57.png)

Next follows the authority, which is separated from the scheme by the character pattern ://. If present the authority includes both the domain (e.g. www.example.com) and the port (80), separated by a colon:
•	The domain indicates which Web server is being requested. Usually this is a domain name, but an IP address may also be used (but this is rare as it is much less convenient).
•	The port indicates the technical "gate" used to access the resources on the web server. It is usually omitted if the web server uses the standard ports of the HTTP protocol (80 for HTTP and 443 for HTTPS) to grant access to its resources. Otherwise it is mandatory.


Path to resource

![pathtoresource](https://user-images.githubusercontent.com/64431648/181002705-51663a65-c4e6-4285-92d4-097ada63e5be.png)

/path/to/myfile.html is the path to the resource on the Web server. In the early days of the Web, a path like this represented a physical file location on the Web server. Nowadays, it is mostly an abstraction handled by Web servers without any physical reality.
Parameters

?key1=value1&key2=value2 are extra parameters provided to the Web server. Those parameters are a list of key/value pairs separated with the & symbol. The Web server can use those parameters to do extra stuff before returning the resource. Each Web server has its own rules regarding parameters, and the only reliable way to know if a specific Web server is handling parameters is by asking the Web server owner.

Anchor 

![anchor](https://user-images.githubusercontent.com/64431648/181002777-fc9ea2fb-de09-443d-a640-2db77ad7f68f.png)

#SomewhereInTheDocument is an anchor to another part of the resource itself. An anchor represents a sort of "bookmark" inside the resource, giving the browser the directions to show the content located at that "bookmarked" spot. On an HTML document, for example, the browser will scroll to the point where the anchor is defined; on a video or audio document, the browser will try to go to the time the anchor represents. It is worth noting that the part after the #, also known as the fragment identifier, is never sent to the server with the request.




Difference between URL and Domain Name

The major difference between both is that the URL is a complete address. URL tells about the method through which information should exchange, the path after reaching that website. Whereas the domain name is part of a URL.
A domain name with more information is a URL.

DNS lookup to find IP address

After hitting the URL, the first thing that needs to happen is to resolve IP address associated with the domain name. DNS helps in resolving this. DNS is like a phone book and helps us to provide the IP address that is associated with the domain name just like our phone book gives a mobile number which is associated with the person’s name.

![dns](https://user-images.githubusercontent.com/64431648/181002847-467b9f44-c4bb-48a6-9f14-51a4b0b62cb0.png)

This is the overview, but there are four layers through which this domain name query goes through.

Let’s understand the steps:
1. After hitting the URL, the browser cache is checked. As browser maintains its DNS records for some amount of time for the websites you have visited earlier. Hence, firstly, DNS query runs here to find the IP address associated with the domain name.
2. The second place where DNS query runs in OS cache followed by router cache.
3. If in the above steps, a DNS query does not get resolved, then it takes the help of resolver server. Resolver server is nothing but your ISP (Internet service provider). The query is sent to ISP where DNS query runs in ISP cache.
4. If in 3rd steps as well, no results found, then request sends to top or root server of the DNS hierarchy. There it never happens that it says no results found, but actually it tells, from where this information you can get. If you are searching IP address of the top level domain (.com,.net,.Gov,. org). It tells the resolver server to search TLD server (Top level domain).
5. Now, resolver asks TLD server to give IP address of our domain name. TLD stores address information of domain name. It tells the resolver to ask it to Authoritative Name server.
6. The authoritative name server is responsible for knowing everything about the domain name. Finally, resolver (ISP) gets the IP address associated with the domain name and sends it back to the browser.
After getting an IP address, resolver stores it in its cache so that next time, if the same query comes then it does not have to go to all these steps again. It can now provide IP address from their cache.
This is all about the steps that is followed to resolve IP address that is associated with the domain name. 
Have a look below to better understand:

![dns_resolve](https://user-images.githubusercontent.com/64431648/181002880-c45c52e4-9141-4bb3-b7df-9795fbea5c0e.png)


TCP connection initiates with the server by Browser

Once the IP address of the computer (where your website information is there) is found, it initiates connection with it. To communicate over the network, internet protocol is followed. TCP/IP is most common protocol. A connection is built between two using a process called ‘TCP 3-way handshake’. Let’s understand the process in brief:
1. A client computer sends a SYN message means, whether second computer is open for new connection or not.
2. Then another computer, if open for new connection, it sends acknowledge message with SYN message as well.
3. After this, first computer receives its message and acknowledge by sending an ACK message.
To better  understand, look below diagram.

![process](https://user-images.githubusercontent.com/64431648/181002992-693324b2-13fd-4c48-ba76-508c998519c2.png)

Communication Starts (Request Response Process)

Finally, the connection is built between client and server. Now, they both can communicate with each other and share information. After successful connection, browser (client) sends a request to a server that I want this content. The server knows everything of what response it should send for every request. Hence, the server responds back. This response contains every information that you requested like web page, status-code, cache-control, etc. Now, the browser renders the content that has been requested.



The browser's high level structure:
The browser's main components are:
1.	The user interface: this includes the address bar, back/forward button, bookmarking menu, etc. Every part of the browser display except the window where you see the requested page.
2.	The browser engine: marshals actions between the UI and the rendering engine.
3.	The rendering engine: responsible for displaying requested content. For example if the requested content is HTML, the rendering engine parses HTML and CSS, and displays the parsed content on the screen.
4.	Networking: for network calls such as HTTP requests, using different implementations for different platform behind a platform-independent interface.
5.	UI backend: used for drawing basic widgets like combo boxes and windows. This backend exposes a generic interface that is not platform specific. Underneath it uses operating system user interface methods.
6.	JavaScript interpreter. Used to parse and execute JavaScript code.
7.	Data storage. This is a persistence layer. The browser may need to save all sorts of data locally, such as cookies. Browsers also support storage mechanisms such as local Storage, IndexedDB, WebSQL and Filesystem.
![layers](https://user-images.githubusercontent.com/64431648/180996417-c76d47d4-f900-4cd4-bfc0-d77e87552b4e.png)

Rendering engine and its use.
The main flow:

The rendering engine will start getting the contents of the requested document from the networking layer. This will usually be done in 8K chunks.
After that this is the basic flow of the rendering engine:
The rendering engine will start parsing the HTML document and turn the tags to DOM nodes in a tree called the "content tree". It will parse the style data, both in external CSS files and in style elements. The styling information together with visual instructions in the HTML will be used to create another tree - the render tree.
The render tree contains rectangles with visual attributes like color and dimensions. The rectangles are in the right order to be displayed on the screen.
After the construction of the render tree it goes through a "layout" process. This means giving each node the exact coordinates where it should appear on the screen. The next stage is painting - the render tree will be traversed and each node will be painted using the UI backend layer.
It's important to understand that this is a gradual process. For better user experience, the rendering engine will try to display contents on the screen as soon as possible. It will not wait until all HTML is parsed before starting to build and layout the render tree. Parts of the content will be parsed and displayed, while the process continues with the rest of the contents that keeps coming from the network.

Parsers (HTML, CSS, etc):

Parsing is a very significant process within the rendering engine. Parsing a document means translating it to some structure that makes sense - something the code can understand and use. The result of parsing is usually a tree of nodes that represent the structure of the document. It is called a parse tree or a syntax tree.
Parsing is based on the syntax rules the document obeys - the language or format it was written in. Every format you can parse must have deterministic grammar consisting of vocabulary and syntax rules. It is called a context free grammar. Human languages are not such languages and therefore cannot be parsed with conventional parsing techniques.
Parsing can be separated into two sub processes - lexical analysis and syntax analysis.
Lexical analysis is the process of breaking the input into tokens. Tokens are the language vocabulary - the collection of valid building blocks. In human language it will consist of all the words that appear in the dictionary for that language.
Syntax analysis is the applying of the language syntax rules.
Parsers usually divide the work between two components - the lexer(sometimes called tokenizer) that is responsible for breaking the input into valid tokens, and the parser that is responsible for constructing the parse tree by analyzing the document structure according to the language syntax rules. The lexer knows how to strip irrelevant characters like white spaces and line breaks.

![parse trees](https://user-images.githubusercontent.com/64431648/180996846-acb39e2e-65a9-422c-b534-9125e62948d9.png)

The parsing process is iterative. The parser will usually ask the lexer for a new token and try to match the token with one of the syntax rules. If a rule is matched, a node corresponding to the token will be added to the parse tree and the parser will ask for another token.
If no rule matches, the parser will store the token internally, and keep asking for tokens until a rule matching all the internally stored tokens is found. If no rule is found then the parser will raise an exception. This means the document was not valid and contained syntax errors.

Translation

Many times the parse tree is not the final product. Parsing is often used in translation - transforming the input document to another format. An example is compilation. The compiler that compiles a source code into machine code first parses it into a parse tree and then translates the tree into a machine code document.

![compilation flow](https://user-images.githubusercontent.com/64431648/180997082-a05d4b0f-2581-420d-85a4-2086c85ee9aa.png)

HTML Parsing

So we have HTML content at the beginning which goes through a process called tokenization, tokenization is a common process in almost every programming language where code is split into several tokens which are easier to understand while parsing. This is where the HTML's parser understands which is the start and which is the end of the tag, which tag it is and what is inside the tag.
Now we know, html tag starts at the top and then the head tag starts before the html ends so we can figure out that the head is inside html and create a tree out of it. Thus we then get something called a parse tree which eventually becomes a DOM tree as shown in the image below:

![htmlparsing](https://user-images.githubusercontent.com/64431648/180997335-24a393b6-bb11-49ec-9d54-1122caad0e48.png)


DOM tree is what we access when we do document.getElementById or document.querySelector in JavaScript.
Just like HTML, CSS goes through a similar process where we have the CSS text and then the tokenization of CSS to eventually create something called a CSSOM or CSS Object Model.
This is what a CSS Object Model looks like:

![cssparcing](https://user-images.githubusercontent.com/64431648/180997371-170d757a-2964-4a47-9fd7-607c48fd701c.png)


now we have DOM and CSSOM so we got every information that is required to get our screens painted


Script Processors

While the CSS is being parsed and the CSSOM created, other assets, including JavaScript files, are downloading (thanks to the preload scanner). JavaScript is interpreted, compiled, parsed and executed. The scripts are parsed into abstract syntax trees. Some browser engines take the Abstract Syntax Tree and pass it into an interpreter, outputting bytecode which is executed on the main thread.


Tree constructiong

Processing the html and body tags results in the construction of the render tree root. The root render object corresponds to what the CSS spec calls the containing block - the top most block that contains all other blocks. Its dimensions are the viewport - the browser window display area dimensions. Firefox calls it ViewPortFrame. This is the render object that the document point to. The rest of the tree is constructed as a DOM nodes insertion.


Order of script processing

The model of the web is synchronous. Authors expect scripts to be parsed and executed immediately when the parser reaches a <script> tag. The parsing of the document halts until the script was executed. If the script is external then the resource must be first fetched from the network - this is also done synchronously, the parsing halts until the resource is fetched. Authors could mark the script as "defer" and thus it will not halt the document parsing and will execute after it is parsed. HTML5 adds an option to mark the script as asynchronous so it will be parsed and executed by a different thread.


Layout
  
The layout is where the elements are marked on the screen. The layout includes all the calculations and mathematics behind an element's position so it takes all the properties related to the position (height, width, position, top left right bottom, etc) from The Render Tree and places the elements on the screen.
  
Paint
  
After Layout, a Paint happens. Paint takes properties like color, background-color, border-color, box-shadow, etc. to paint the screen with colors.
After the paint, we see the content on the screen and the first time we see something other than a white screen is called 'First Paint'. The term First Paint is used in performance reports to show how long your website took to show something on the screen.
