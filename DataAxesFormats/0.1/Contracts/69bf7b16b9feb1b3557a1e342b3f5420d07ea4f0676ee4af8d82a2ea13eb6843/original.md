```
@kwdef struct Contract
    is_relaxed::Bool = false
    axes::Maybe{ContractAxes} = nothing
    data::Maybe{ContractData} = nothing
end
```

The contract of a computational tool, specifing the `axes` and and `data`. If `is_relaxed`, this allows for additional inputs and/or outputs; this is typically used when the computation has query parameters, which may need to access such additional data, or when the computation generates a variable set of data.

!!! note
    When a function calls several functions in a row, you can compute its contract by using [`function_contract`](@ref DataAxesFormats.Computations.function_contract) on them and then combining the results in their invocation order using `|>`.

