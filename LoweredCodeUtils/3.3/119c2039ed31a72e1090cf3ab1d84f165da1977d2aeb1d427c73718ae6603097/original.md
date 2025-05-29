```
selective_eval!([interp::Interpreter=RecursiveInterpreter()], frame::Frame, isrequired::AbstractVector{Bool}, istoplevel=false)
```

Execute the code in `frame` in the manner of `JuliaInterpreter.finish_and_return!`, but skipping all statements that are marked `false` in `isrequired`. See [`lines_required`](@ref). Upon entry, if needed the caller must ensure that `frame.pc` is set to the correct statement, typically `findfirst(isrequired)`. See [`selective_eval_fromstart!`](@ref) to have that performed automatically.

`isrequired` pertains only to `frame` itself, not any of its callees.

This will return either a `BreakpointRef`, the value obtained from the last executed statement (if stored to `frame.framedata.ssavlues`), or `nothing`. Typically, assignment to a variable binding does not result in an ssa store by JuliaInterpreter.
