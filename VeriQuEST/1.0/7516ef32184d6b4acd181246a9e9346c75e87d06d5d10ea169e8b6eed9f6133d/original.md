```
throw_error(::ProbabilityExceedsOneError)
```

Throws an error when a probability greater than 1 is encountered.

# Examples

```julia
throw_error(ProbabilityExceedsOneError()) # Throws an error with the message "Probability is greater than 1 (hint: not a probability and threw an error)"
```
