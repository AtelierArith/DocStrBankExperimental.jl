General usage:

```julia
@check :name_of_backend config_dictionary begin
    # the prelimnary code
end begin
    # the actual code you want to do perf testing for
end
```

Outputs a `CheckerResult` which can be used with other functions.  
