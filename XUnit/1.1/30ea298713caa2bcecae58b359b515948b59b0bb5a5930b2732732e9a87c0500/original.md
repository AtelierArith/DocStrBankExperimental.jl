```
@testcase "test-case name" begin ... end
@testcase [before_each=()->...] [after_each=()->...] [metrics=DefaultTestMetrics]
          [success_handler=(testcase)->...] [failure_handler=(testcase)->...]
          [xml_report=false] [html_report=false] "test-case" begin ... end
```

Defines a self-contained test-case.

Test-cases are gathered at scheduling time and will get executed using a test-runner. As a test-runner can run tests in any order (and even on multiple threads/processes), it's strongly advised that test-cases do not depend on each other.

## Keyword Arguments

`@testcase` takes four additional parameters:

  * `metrics`: a custom `TestMetrics` type
  * `success_handler`: a function to run after a successful handling of all tests. This function accepts the test-suite as an argument. This argument only works for the top-most `@testcase`.
  * `failure_handler`: a function to run after a failed handling of all tests. This function accepts the test-suite as an argument. This argument only works for the top-most `@testcase`.
  * `xml_report`: whether to produce the XML output file at the end. This argument only works for the top-most `@testcase`
  * `html_report`: whether to produce the HTML output file at the end. This argument only works for the top-most `@testcase`
