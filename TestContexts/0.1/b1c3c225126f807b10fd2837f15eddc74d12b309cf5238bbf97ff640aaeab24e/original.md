```
test_set(body::Function, name::String, data...)
```

Similar to @testset but uses the global `tc` test context for running tests under the given `name`. The optional `data` must a series of zero or more entries, each in the format `property => value` where `property` is a symbol and `value` is a `PropertyValue`.

Nesting test sets is allowed. This is a common pattern for incrementally setting up a test environment for the actual test cases. In BDD terminology, a test set is similar to the "given" or "when" clauses.

The property values are not accessible (yet). See `test_case` for actually accessing the data.
