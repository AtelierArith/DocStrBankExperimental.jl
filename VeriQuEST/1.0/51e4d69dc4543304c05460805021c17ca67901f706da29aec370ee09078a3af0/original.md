```
throw_error(::ProbabilityLessThanZeroError)
```

Throws an error when a probability less than zero is encountered.

# Examples

```julia
throw_error(ProbabilityLessThanZeroError()) # Throws an error with the message "Probability is less than 0 (hint: not a probability and threw an error)"
```
