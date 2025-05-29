```
throw_error(::ProbabilityExceedsThreeQuartersError)
```

Throws an error when a probability greater than 3/4 is encountered, typically in relation to noise model limitations.

# Examples

```julia
throw_error(ProbabilityExceedsThreeQuartersError()) # Throws an error with the message "Probability is greater than 3/4 (hint: error thrown in relation to noise model limitations)"
```
