```
TestItem
```

A single, independently runnable group of tests. Used to wrap tests that must be run together, similar to a `@testset`, but encapsulating those test in their own module. Should only be created via the `@testitem` macro.
