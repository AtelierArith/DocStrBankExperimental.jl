```
ReportingTestSet
```

Custom `AbstractTestSet` type designed to be used by `TestReports.jl` for creation of JUnit XMLs.

Does not throw an error when a test fails or has an error. Upon `finish`ing, a `ReportingTestSet` will display the default test output, and then flatten to a structure that is suitable for report generation.

It is designed to be wrapped around a package's `runtests.jl` file and this is assumed when both the test results are displayed and when the `TestSet` is flatted upon `finish`. See `bin/reporttests.jl` for an example of this use. `ReportingTestSet`s are not designed to be used directly in a package's tests, and this is not recommended or supported.

A `ReportingTestSet` has the `description` and `results` fields as per a `DefaultTestSet`, and has the following additional fields:

  * `testset_properties`: used to record testset properties to be inserted into the report.
  * `test_properties`: used to record test properties to be inserted into the report.
  * `start_time::DateTime`: the start date and time of the testing (local system time).
  * `time_taken::Millisecond`: the time taken in milliseconds to run the `TestSet`.
  * `last_record_time::DateTime`: the time when `record` was last called.
  * `hostname::String`: the name of host on which the testset was executed.

See also: [`flatten_results!`](@ref), [`record_testset_property`](@ref), [`record_testset_property`](@ref), and [`report`](@ref).
