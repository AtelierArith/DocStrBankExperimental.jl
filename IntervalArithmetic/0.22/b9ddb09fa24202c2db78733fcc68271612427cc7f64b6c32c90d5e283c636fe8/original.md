```
ExactReal{T<:Real} <: Real
```

Real numbers with the assurance that they precisely correspond to the number described by their binary form. The purpose is to guarantee that a non interval number is exact, so that `ExactReal` can be used with `Interval` without producing the "NG" flag.

!!! danger
    By using `ExactReal`, users acknowledge the responsibility of ensuring that the number they input corresponds to their intended value. For example, `ExactReal(0.1)` implies that the user knows that $0.1$ can not be represented exactly as a binary number, and that they are using a slightly different number than $0.1$. To help identify the binary number, `ExactReal` is displayed without any rounding.

    ```julia
    julia> ExactReal(0.1)
    ExactReal{Float64}(0.1000000000000000055511151231257827021181583404541015625)
    ```

    In case of doubt, [`has_exact_display`](@ref) can be use to check if the string representation of a `Real` is equal to its binary value.


# Examples

```jldoctest
julia> setdisplay(:full);

julia> 0.5 * interval(1)
Interval{Float64}(0.5, 0.5, com)_NG

julia> ExactReal(0.5) * interval(1)
Interval{Float64}(0.5, 0.5, com)

julia> [1, interval(2)]
2-element Vector{Interval{Float64}}:
 Interval{Float64}(1.0, 1.0, com)_NG
 Interval{Float64}(2.0, 2.0, com)

julia> [ExactReal(1), interval(2)]
2-element Vector{Interval{Float64}}:
 Interval{Float64}(1.0, 1.0, com)
 Interval{Float64}(2.0, 2.0, com)
```

See also: [`@exact`](@ref).
