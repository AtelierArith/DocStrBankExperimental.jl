```
throw_error(::ProbabilityExceedsNoErrorExceeded)
```

Throws an error when a probability is greater than no error from 1.

# Examples

```julia
throw_error(ProbabilityExceedsNoErrorExceeded()) # Throws an error with the message "Probability is greater than no error from 1."
```
