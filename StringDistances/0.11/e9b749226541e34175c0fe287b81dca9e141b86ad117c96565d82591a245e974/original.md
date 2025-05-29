TokenMax(dist)

Creates the `TokenMax{dist}` distance, which is only defined on AbstractStrings.

`TokenMax{dist}` normalizes the distance `dist` and returns the minimum of the distance, its [`Partial`](@ref) modifier, its [`TokenSort`](@ref) modifier, and its  [`TokenSet`](@ref) modifier, with penalty terms depending on the strings lengths.

### Examples

```julia-repl
julia> s1 = "New York Mets vs Atlanta"
julia> s2 = "Atlanta Braves vs New York Mets"
julia> evaluate(TokenMax(RatcliffObershelp()), s1, s2)
0.05
```
