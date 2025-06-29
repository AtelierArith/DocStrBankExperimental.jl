# ApproximateRelations.jl

A Julia package for performing approximate comparisons between real numbers with customizable tolerance levels at a global, function, block or individual comparison level.

## Main Features:

  * Approximate comparisons using `approx` function and `@approx` macro
  * Support for all standard comparison operators (`<`, `<=`, `>`, `>=`, `==`, `!=`)
  * Global tolerance setting with `set_approx!` and `get_approx`
  * Local tolerance setting for blocks, functions, and individual expressions
  * Chained comparison support (e.g., `approx(0, <, x, 1)`, `@approx 0 < x < 1`)
  * Integration with testing frameworks via `@test` and `@testset` compatibility
  * Support for `iszero` and `isone` approximate checks
  * Macro expansion filtering to control which macros are expanded during processing
  * Flexible use in assertions and conditional statements

The package provides a powerful and flexible way to handle real number comparisons and equality checks with customizable precision, making it ideal for numerical computations and testing scenarios where exact equality is impractical.
