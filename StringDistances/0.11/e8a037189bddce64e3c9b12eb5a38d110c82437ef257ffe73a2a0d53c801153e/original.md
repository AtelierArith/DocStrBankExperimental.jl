```
findnearest(s, itr, dist::Union{StringMetric, StringSemiMetric}) -> (x, index)
```

`findnearest` returns the value and index of the element of `itr` that has the  lowest distance with `s` according to the distance `dist`. 

It is particularly optimized for [`Levenshtein`](@ref) and [`DamerauLevenshtein`](@ref) distances  (as well as their modifications via [`Partial`](@ref), [`TokenSort`](@ref), [`TokenSet`](@ref), or [`TokenMax`](@ref)).

### Examples

```julia-repl
julia> using StringDistances
julia> s = "Newark"
julia> iter = ["New York", "Princeton", "San Francisco"]
julia> findnearest(s, iter, Levenshtein())
("NewYork", 1)
julia> findnearest(s, iter, Levenshtein(); min_score = 0.9)
(nothing, nothing)
```
