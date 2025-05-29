```
throw_warning(::UntestedKrausFunction)
```

Throws a warning when a Kraus operator is not tested, specifically transalting a pointer index from Julia to C, use at peril till function goes away.

# Examples

```julia
throw_warning(UntestedKrausFunction()) # Throws a warning with the message "Kraus operator is not tested, specifically transalting a pointer index from Julia to C, use at peril till function goes away"
```
