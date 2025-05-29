```
test_case(body::Function, name::String, data...)
```

Similar to `test_set` but is used to wrap actual `@test` code. Allows access to any data previously setup by the containing `test_set` calls, if any, or in the `test_case` call itself. The properties data is available during the test by accessing `tc.property`. A separate instance is created (lazily) for any private data for each test case. If a `finalize` function was specified, it is invoked to properly dispose of the data at the end of the test case.

Nesting a test set or a test case inside a test case is forbidden. That is, a test case is expected to actually test some specific scenario which was set up by the containing test sets. In BDD terminology, a test case is similar to the "then" clause.

If any `test_patterns` were specified, and the full `test_name` does not match any of these patterns, then the test case is silently ignored. Otherwise, the test name is logged using `@debug` before the test case code is executed.
