```
TestItemRunner
```

This module provides functionalities to run `@testitem` tests in a Julia package,  as part of the TestItemRunner.jl package. It supports running individual test items,  which are self-contained units of code written within `@testitem` macros.

# Key Features

  * Provides a mechanism to run individual test items in isolation, ensuring that each  test item is executed in a new Julia module.
  * Supports filtering of test items based on custom criteria, and verbose output during testing.
  * Integrates with the base test system, and can be utilized in conjunction with the Julia VS Code  extension or as a standalone test runner.
