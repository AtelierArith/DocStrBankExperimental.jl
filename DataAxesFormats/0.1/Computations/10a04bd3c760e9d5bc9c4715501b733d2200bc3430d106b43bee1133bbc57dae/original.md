```
@computation function something(...)
    return ...
end

@computation Contract(...) function something(daf::DafWriter, ...)
    return ...
end

@computation Contract(...) Contract(...) function something(
    first::DafReader/DafWriter, second::DafReader/DafWriter, ...
)
    return ...
end
```

Mark a function as a `Daf` computation. This has the following effects:

  * It verifies that the `Daf` data satisfies the [`Contract`](@ref), when the computation is invoked and when it is complete (using [`verify_input`](@ref) and [`verify_output`](@ref)).
  * It stashes the contract(s) (if any) in a global variable. This allows expanding [`CONTRACT`](@ref) in the documentation string (for a single contract case), or [`CONTRACT1`](@ref) and [`CONTRACT2`](@ref) (for the dual contract case).
  * It stashes the default value of named arguments. This allows expanding [`DEFAULT`](@ref) in the documentation string, which is especially useful if these defaults are computed, read from global constants, etc.
  * It logs the invocation of the function (using `@debug`), including the actual values of the named arguments (using [`depict`](@ref)).

!!! note
    For each [`Contract`](@ref) parameter (if any), there needs to be a [`DafReader`](@ref) or [`DafWriter`](@ref), which the contract(s) will be applied to. These parameters should be the initial positional parameters of the function.

