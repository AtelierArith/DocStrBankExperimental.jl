```
check(
    φ::SoleLogics.SyntaxTree,
    i::SoleLogics.LogicalInstance{<:AbstractModalLogiset{W,<:U}},
    w::Union{Nothing,AnyWorld,<:AbstractWorld} = nothing;
    kwargs...
)::Bool
```

Check whether a formula `φ` holds for a given instance `i_instance` of a logiset `X`, on a world `w`. Note that the world can be elided for grounded formulas (see [`isgrounded`](@ref)).

This implementation recursively evaluates the subformulas of `φ` and use memoization to store the results using Emerson-Clarke algorithm. The memoization structure is either the one stored in `X` itself (if `X` supports memoization) or a structure passed as the `use_memo` argument. If `X` supports onestep memoization, then it will be used for specific diamond formulas, up to an height equal to a keyword argument `memo_max_height`.

# Arguments

  * `φ::SoleLogics.SyntaxTree`: the formula to check.
  * `i::SoleLogics.LogicalInstance{<:AbstractModalLogiset{W,<:U}}`: the instance of the logiset to check in.
  * `w::Union{Nothing,AnyWorld,<:AbstractWorld} = nothing`: the world to check in. If `nothing`, the method checks in all worlds of the instance.

# Keyword arguments

  * `use_memo::Union{Nothing,AbstractMemoset{<:AbstractWorld},AbstractVector{<:AbstractDict{<:FT,<:AbstractWorlds}}} = nothing`: the memoization structure to use. If `nothing`, the method uses the one stored in `X` if `X` supports memoization. If `AbstractMemoset`, the method uses the `i_instance`-th element of the memoization structure. If `AbstractVector`, the method uses the `i_instance`-th element of the vector.
  * `perform_normalization::Bool = true`: whether to normalize the formula before checking it.
  * `memo_max_height::Union{Nothing,Int} = nothing`: the maximum height up to which onestep memoization should be used. If `nothing`, the method does not use onestep memoization.
  * `onestep_memoset_is_complete = false`: whether the onestep memoization structure is complete (i.e. it contains all possible values of the metaconditions in the structure).
