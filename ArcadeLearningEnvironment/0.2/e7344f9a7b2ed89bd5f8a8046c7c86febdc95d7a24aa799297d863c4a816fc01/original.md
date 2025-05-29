```
setLoggerMode!(mode::Symbol)
```

Sets the mode for the Logger for the ALE instance. Three modes(::Symbol) are available.     :info    ==> logs all details and information     :warning ==> logs warnings and errors     :error   ==> logs errors only

# Example

```julia-repl
julia> setLoggerMode!(:info)
```
