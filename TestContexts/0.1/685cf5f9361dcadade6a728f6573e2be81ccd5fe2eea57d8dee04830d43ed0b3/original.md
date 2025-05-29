```
PrivateValue(make::Function, finalize::Union{Function,Nothing}=nothing)
```

A private value will be (lazily) re-created for each test (that accesses it) by invoking the `make` function. This value can be mutated at will by the test case without affecting any other test case. If the `finalize` function was specified, it is invoked at the end of each test case (that accessed the value) and is given the value so it can be properly disposed of.
