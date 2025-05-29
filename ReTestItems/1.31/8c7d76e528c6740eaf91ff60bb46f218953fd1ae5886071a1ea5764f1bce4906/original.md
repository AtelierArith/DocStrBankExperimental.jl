```
@testsetup module MyTestSetup
    # code that can be shared between @testitems
end
```

A module only used for tests, and which `@testitem`s can depend on.

Useful for setup logic that is used across multiple test items. The setup will run once, before any `@testitem` that requires it is executed. If running with multiple processes, each test-setup with be run once on each process.

Each test-setup module will live for the lifetime of the tests. Mutable state should be avoided, since the order in which test items run is non-deterministic, and test items may access the same test-setup module concurrently in the same process.

Other than being declared with the `@testsetup` macro, to make then knowable to `@testitem`s, test-setup modules are just like other modules and can import dependencies and export names.

A `@testitem` depends on a `@testsetup` via the `setup` keyword e.g

```
@testitem "MyTests1" setup=[MyTestSetup]
    # tests that require MyTestSetup
end
```
