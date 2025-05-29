```
@exact
```

Wrap every literal numbers of the expression in an [`ExactReal`](@ref). This macro allows defining generic functions, seamlessly accepting both `Number` and [`Interval`](@ref) arguments, without producing the "NG" flag.

!!! danger
    By using [`ExactReal`](@ref), users acknowledge the responsibility of ensuring that the number they input corresponds to their intended value. For example, `ExactReal(0.1)` implies that the user knows that $0.1$ can not be represented exactly as a binary number, and that they are using a slightly different number than $0.1$. To help identify the binary number, `ExactReal` is displayed without any rounding.

    ```julia
    julia> ExactReal(0.1)
    ExactReal{Float64}(0.1000000000000000055511151231257827021181583404541015625)
    ```

    In case of doubt, [`has_exact_display`](@ref) can be use to check if the string representation of a `Real` is equal to its binary value.


# Examples

```jldoctest
julia> setdisplay(:full);

julia> f(x) = 1.2*x + 0.1
f (generic function with 1 method)

julia> f(interval(1, 2))
Interval{Float64}(1.2999999999999998, 2.5, com)_NG

julia> @exact g(x) = 1.2*x + 0.1
g (generic function with 1 method)

julia> g(interval(1, 2))
Interval{Float64}(1.2999999999999998, 2.5, com)

julia> g(1.4)
1.78
```

See also: [`ExactReal`](@ref).
