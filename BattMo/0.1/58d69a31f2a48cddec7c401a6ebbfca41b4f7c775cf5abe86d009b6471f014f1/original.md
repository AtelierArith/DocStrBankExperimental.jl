```
run_battery(inputparams::AbstractInputParams; hook = nothing)
```

Simulate a battery for a given input. The input is expected to be an instance of AbstractInputParams. Such input can be prepared from a json file using the function [`readBattMoJsonInputFile`](@ref).
