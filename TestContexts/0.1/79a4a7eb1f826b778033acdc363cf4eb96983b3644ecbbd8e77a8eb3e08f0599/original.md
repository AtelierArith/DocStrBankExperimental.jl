```
test_name()::AbstractString
```

Return the full name of the current test context. This is a `/`-separated path containing the names of all the nested `test_set` and `test_case` calls. This full name is automatically logged using `@debug` at the start of each test case. It is also matched against any `test_patterns` to allow executing only a specific subset of the tests.
