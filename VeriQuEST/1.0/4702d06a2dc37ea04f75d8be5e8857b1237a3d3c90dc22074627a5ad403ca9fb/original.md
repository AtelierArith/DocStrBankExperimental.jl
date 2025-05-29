```
throw_error(::ProbabilityExceedsOneHalfError)
```

Throws an error when a probability greater than 1/2 is encountered, typically in relation to noise model limitations.

# Examples

```julia
throw_error(ProbabilityExceedsOneHalfError()) # Throws an error with the message "Probability is greater than 1/2 (hint: error thrown in relation to noise model limitations)"
```
