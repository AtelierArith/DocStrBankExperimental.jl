```
InfiniteOpt.internal_semi_infinite_variable(
    vref::InfiniteOpt.SemiInfiniteVariableRef,
    ::Val{:TransData}
    )::InfiniteOpt.SemiInfiniteVariable{InfiniteOpt.GeneralVariableRef}
```

Return the internal semi-infinite variable associated with `vref`, assuming it was added internally during measure expansion at the transcription step. This extends [`InfiniteOpt.internal_semi_infinite_variable`](@ref) as described in its docstring. Errors, if no such variable can be found.
