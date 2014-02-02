# useref

Parse build blocks in HTML files to replace references

Extracted from the grunt plugin [grunt-useref](https://github.com/pajtai/grunt-useref).

## Installation

    npm install useref

## Usage

    useref = require('useref')
    var result = useref(inputHtml)
    // result = [ replacedHtml, { type: { id: [ replacedFiles] }} ]


The build block syntax is `build:type id`. Valid types are `js` and `css`

    <html>
    <head>
      <!-- build:css css/combined.css -->
      <link href="css/one.css" rel="stylesheet">
      <link href="css/two.css" rel="stylesheet">
      <!-- endbuild -->
    </head>
    <body>
      <!-- build:js scripts/combined.js -->
      <script type="text/javascript" src="scripts/one.js"></script>
      <script type="text/javascript" src="scripts/two.js"></script>
      <!-- endbuild -->
    </body>
    </html>

The module would be used with the above sample HTML as follows:

    var result = useref(sampleHtml)

    // [
    //   resultHtml,
    //   {
    //     css: {
    //       'css/combined.css': [ 'css/one.css', 'css/two.css' ]
    //     },
    //     js: {
    //       'scripts/combined.js': [ 'css/one.js', 'css/two.js' ]
    //     }
    //   }
    // ]


The resulting HTML would be:

    <html>
    <head>
      <link rel="stylesheet" href="css/combined.css"/>
    </head>
    <body>
      <script src="scripts/combined.js"></script>
    </body>
    </html>