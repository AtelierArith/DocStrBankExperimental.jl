```
@testset "suite name" begin ... end
@testset [before_each=()->...] [after_each=()->...] [metrics=DefaultTestMetrics]
           [success_handler=(testset)->...] [failure_handler=(testset)->...]
           [xml_report=false] [html_report=false] "suite name" begin ... end
```

Schedules a Test Suite

Please note that `@testset` and `@testset` macros are very similar. The only difference is the top-level `@testset` also runs the test-cases, but a top-level `@testset` does not run its underlying test-cases (and only schedules them). Then, one needs to explicitly call `run_testset` over the result of this macro.

Also, note that the body of a `@testset` always gets executed at scheduling time, as it needs to gather possible underlying `@testcase`s. Thus, it's a good practice to put your tests under a `@testcase` (instead of putting them under a `@testset`), as any tests defined under a `@testset` are executed sequentially at scheduling time.

## Keyword Arguments

`@testset` takes seven additional parameters:

  * `before_each`: a function to run before each underlying test-case
  * `after_each`: a function to run after each underlying test-case
  * `metrics`: a custom `TestMetrics` type
  * `success_handler`: a function to run after a successful handling of all tests. This function accepts the test-suite as an argument. This argument only works for the top-most `@testset`.
  * `failure_handler`: a function to run after a failed handling of all tests. This function accepts the test-suite as an argument. This argument only works for the top-most `@testset`.
  * `xml_report`: whether to produce the XML output file at the end. This argument only works for the top-most `@testset`
  * `html_report`: whether to produce the HTML output file at the end. This argument only works for the top-most `@testset`
