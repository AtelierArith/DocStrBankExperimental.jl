```
full_factorial(parameters...)
full_factorial(parameters...; disallow = filter_function)
```

Generates a test case for every combination of the parameters.

# Examples

```julia
full_factorial([0.1, 0.2, 0.3], ["low", "high"], [false, true])
```

If you specify a filter function, it will remove combinations that are disallowed.
