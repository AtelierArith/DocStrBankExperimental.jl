```
record_test_property(name::AbstractString, value)
```

Associates a property with the tests contained with the testset. The `name` and `value` will be turned into a `<property>` element with the corresponding `<testcase>` element within the JUnit XML report.

Multiple test properties can be assigned within a testset and child testsets will inherit the test properties defined by their parents. If a child testset records a test property with an already used name both properties will be present in the resulting report.

For more details and examples see the documentation for [`record_testset_property`](@ref).

See also: [`record_testset_property`](@ref) and [`test_properties`](@ref).
