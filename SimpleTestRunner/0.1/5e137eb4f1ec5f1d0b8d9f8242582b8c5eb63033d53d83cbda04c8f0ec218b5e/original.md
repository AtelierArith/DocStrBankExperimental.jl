```
testnames(dir::String)
```

List test names found under `dir`.

Test name strings are derived from the relative path of each file under `dir` with a name ending in `_tests.jl`.

For example, if `dir` contains a file named `foo_tests.jl`, a directory named `bar` and a file in the `bar` directory named `baz_tests.jl`, then the list of test names would be `["foo", "bar/baz"]`.
