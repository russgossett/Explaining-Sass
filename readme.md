#Explaining Sass
#####It's all about style, right?
How do we get the code that we spend all this time strategizing, fussing, tweaking, testing, iterating, building to look good? Bootstrap? Foundation? Divshot? 

We all want the code we write to look good…fast! and we want it to be easy to write. _Enter Sass_.


##What is it?
#####S.A.SS = Syntactically Awesome StyleSheets
#####SCSS = Sassy CSS (the newer syntax that you will see most often)

Just like the website says SCSS "is a superset of CSS3's syntax…every valid CSS3 stylesheet is valid SCSS as well." SASS is older, and inspired by HAML meaning it follows an indentation specificity (like Jade or Slim for producing markup). Since I have been writing in the CSS syntax I feel most comfortable with writing SCSS instead of SASS, but feel free to experiment. Whatever the case, their both referred to as Sass. 

http://sass-lang.com

##Why is it so awesome?
- It makes CSS fun again
- Object Oriented CSS (OOCSS)
- Great for rapid prototyping

## How do we get it running?
Install it using the ruby gem…

_SASS_: 
          
		$gem install sass
		navigate to your project folder
		$scss --watch file_name.scss:file_name.css
		
this also works

		$sass --watch scss_folder:css_folder

_COMPASS_:  
  
		$sudo gem install compass
		navigate to your project folder
		$compass create sass_folder_name
		$compass watch sass_folder_name

Compass Plug: When created for a project, it creates a config.rb file so you can edit how sass spits out css (nested, compressed, etc.)

##How do I use it?
###variables 
_STRUCTURE:_ 

		$name_of_variable: argument;
		
_EXAMPLE:_

		$app-blue: #06C;
		$app-red: darkred;
		$app-gray: rgba(0,0,0,.75);
		
		color: $app-red;
		
		$margin: 5px;
		h1 {$margin - 5px}


###nesting
_STRUCTURE:_

		parent_selector {
		     child_selector {}
		}

_EXAMPLE (CSS3):_

		.container {}
		    .container header {}
		      .container header ul {}
		           .container header ul li {}
		               .container header ul li a {}
		                    .container header ul li a:hover {}

_EXAMPLE (SCSS):_

		 .container {
				width:100%;
				margin:0px auto;
				@media screen and (min-width: 600px) {
				    width:60%;
				    font-size:120%;
				}
		     header {
          ul {
             li {
               a {}
               :hover {}
               &:after {}
               &:before {}
               &:first-child {}
          }
			}

###mixins
_STRUCTURE:_

    @mixin name_of_mixin(argument variable: default argument) {}
    @inclue name_of_mixin;
    
Let's create a mixing for those unruly vendor pre-fixes and border radius.

_EXAMPLE:_

    @mixin border-radius($radius: 20px) {
	    -webkit-border-radius: $radius;
	    -moz-border-radius: $radius;
	    -ms-border-radius: $radius;
	    -o-border-radius: $radius;
	    -khtml-border-radius: $radius;
	    border-radius: $radius;
    }

		.header {
		@include border-radius;
		}

##What more could I learn and where?
###What is Compass?
Compass is the first Sass-based framework. Compass is like using Javascript without using jQuery. Just like when you were learning jQuery and you'd refer to the documentation to see if they had an easy way to prepend. And then you go to the site and document is painfully obvious. See jquery api: Prepend. Compass is the exact same. If you're looking for a way to generate typographic hierarchy without loading the entire Twitter Bootstrap (I'm not looking at anyone in particular; Teddy!)

You can read all about Compass on their fantastically documented website

http://compass-style.org/


###Using conditionals (@if and @else)

		$break-small: 320px;
		$break-large: 1024px;
		
		@mixin respond-to($media) { 
		 
			@if $media == handhelds {
				@media only screen and (max-width: $break-small) { @content; }  
		  }  

			@else if $media == medium-screens {    
				@media only screen and (min-width: $break-small + 1) and (max-width: $break-large - 1) { @content; }  
			}  
			@else if $media == wide-screens {    
				@media only screen and (min-width: $break-large) { @content; }  
			}
		}
		
		img.profile {  
			float: left;  
			width: 250px;  
			@include respond-to(handhelds) { width: 100% ;}  
			@include respond-to(medium-screens) { width: 125px; } 
			@include respond-to(wide-screens) { float: none; }
		} 

###Helpful links & tutorials (video):
- http://sass-lang.com/
- http://thesassway.com/
- http://www.youtube.com/watch?v=fbVD32w1oTo
- https://medium.com/what-i-learned-building/b4daab987fb0
- http://www.codeschool.com/paths/html-css#sass
