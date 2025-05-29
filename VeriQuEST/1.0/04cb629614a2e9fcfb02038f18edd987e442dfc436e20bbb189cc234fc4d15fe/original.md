```
throw_error(::ProbabilityExceedsFifteenSixteensError)
```

Throws an error when a probability greater than 15/16 is encountered, typically in relation to noise model limitations.

# Examples

```julia
throw_error(ProbabilityExceedsFifteenSixteensError()) # Throws an error with the message "Probability is greater than 15/16 (hint: error thrown in relation to noise model limitations)"
```
