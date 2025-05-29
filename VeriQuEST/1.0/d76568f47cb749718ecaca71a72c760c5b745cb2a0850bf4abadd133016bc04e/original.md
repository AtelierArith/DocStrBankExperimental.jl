```
throw_error(::ExceededNumKrausOperators)
```

Throws an error when more Kraus operators were presented than allowed.

# Examples

```julia
throw_error(ExceededNumKrausOperators()) # Throws an error with the message "More Kraus operators were presented than allowed. Check again."
```
