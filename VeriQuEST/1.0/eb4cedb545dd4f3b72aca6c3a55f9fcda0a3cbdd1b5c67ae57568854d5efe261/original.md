```
throw_warning(::FunctionNotMeantToBeUsed)
```

Throws a warning message when a function that is not meant to be used anymore is called.

# Examples

```julia
throw_warning(FunctionNotMeantToBeUsed()) # Throws a warning with a specific message
```
