# protractor-multicapabilities-htmlreporter_v2

Utility to generate html report for protractor multi capabilities with data provider. Use case is when
you want to execute the same test in multiple variants/versions and then you need to report the execution
separately.

## Installation

 ```
 npm install protractor-multicapabilities-htmlreporter_v2
 ```

## Protractor Usage

Execute the script in protractor afterLaunch callback. [A callback function called once 
all tests have finished running and the WebDriver instance has been shut down.]

```

afterLaunch: function() {
var reporter = require('protractor-multicapabilities-htmlreporter_v2');
reporter.generateHtmlReport('./ptor-out.json','Automation Results','./report.html');
}

```

## Configurations

```
Add the below config for generating output for results in json format

resultJsonOutputFile: 'ptor-out.json'

Make sure test description follows the below format and json output file contains description 
in the same format.

Sample test file below, this below example shows hardcoded browser values, you can dynamically pass 
browsername and version using getProcessedConfig() as browser.params in onPrepare callback function.

...
it("Version1|Product_Page|iPhone|8.0" ,function () { 
...

it("Version2|Product_Page|iPhone|8.0" ,function () { 
...
```

## Sample Protractor JSON output file
```
[
    {
        "description": "Version1|Category_Page|iPhone|8.0",
        "assertions": [],
        "duration": 4544
    },
    {
        "description": "Version2|Product_Page|iPhone|8.0",
        "assertions": [],
        "duration": 5898
    }
]
```
## Html Report

![Alt text](/examples/html-report.png?raw=true "Multicapabilities Html Report")

## Release History

* 0.0.1 Initial release
