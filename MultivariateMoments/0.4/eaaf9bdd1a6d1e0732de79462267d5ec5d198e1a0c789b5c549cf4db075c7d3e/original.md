```
struct FallbackRank{T,D,F} <: RankCheck
    tol::T
    default::D
    fallback::F
end
```

Defaults to checking the rank with `default` and falls back to `fallback` if the [`doubt`](@ref) is strictly larger than `tol`. By default, `fallback` is [`UserRank`](@ref).

## Example

The advantage of [`UserRank`](@ref) is that the user get to see if the rank check is ambiguous and act accordingly. The downside is that it might be cumbersome if there are many rank checks to do. With `FallbackRank`, the user only has to sort out the tricky ones. In the example below, the first example is handled by [`LargestDifferentialRank`](@ref). For the second one, the user sees that this is a tricky choice and can manually choose one of the two ranks, then see the result of the rest of his code using this value of the code and then choose the other rank and see the impact of this different choice.

```julia
julia> check = FallbackRank(1e-1, LargestDifferentialRank())
FallbackRank{Float64, LargestDifferentialRank, UserRank}(0.1, LargestDifferentialRank(), UserRank(8))

julia> rank_from_singular_values([1, 1e-2, 5e-2, 1e-3, 1e-6, 5e-7], check)
4

julia> rank_from_singular_values([1, 1e-2, 5e-2, 1e-3, 5e-6, 5e-7], check)
Choose the last significant singular value:
 > 1.0
   0.01
   0.05
   0.001
   5.0e-6
   5.0e-7
1

julia> rank_from_singular_values([1, 1e-2, 5e-2, 1e-3, 5e-6, 5e-7], check)
Choose the last significant singular value:
   1.0
   0.01
   0.05
 > 0.001
   5.0e-6
   5.0e-7
4
```
