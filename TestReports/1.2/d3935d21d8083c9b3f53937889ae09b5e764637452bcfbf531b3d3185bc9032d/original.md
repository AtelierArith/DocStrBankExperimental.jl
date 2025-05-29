```
report(ts::AbstractTestSet) -> XMLDocument
```

Produce an JUnit XML report details about the contained `TestSet`s and `Result`s. As the JUnit XML schema does not allow nested `testsuite` elements the report will flatten the hierarchical `TestSet` structure. Each `TestSet` will become a `testsuite` element and each `Result` will become a `testcase` element.

A `Result` will only be reported once within its parent `TestSet` to avoid having duplicate entries within the report and avoid problems with total test counts not matching Julia output.

All `AbstractTestSet`s contained within `ts` must have a `description::AbstractString` field and an iterable `results` field.
