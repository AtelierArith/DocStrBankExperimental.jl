```
assert_comment(condition, message)
```

Asserts that a given `condition` is true. If the `condition` is false, the function throws an AssertionError with the provided `message`.

# Arguments

  * `condition`: The condition to be checked.
  * `message`: The message to be displayed if the assertion fails.

# Examples

```julia
assert_comment(1 == 1, "Numbers are not equal") # Does not throw an error
assert_comment(1 == 2, "Numbers are not equal") # Throws an AssertionError
```
