```
struct HagerZhangLineSearch{T<:Real} <: AbstractLineSearch
HagerZhangLineSearch(; c₁::Real = 1//10, c₂::Real = 9//10, ϵ::Real = 1//10^6,
                    θ::Real = 1//2, γ::Real = 2//3, ρ::Real = 5//1)
```

Constructs a Hager-Zhang line search object with the specified parameters.

## Arguments:

  * `c₁::Real`: Parameter for the (approximate) first Wolfe condition (Armijo rule), controlling sufficient decay of function value: c₁ < 1/2 < c₂. Default is `1//10`.
  * `c₂::Real`: Parameter for the second Wolfe condition (curvature contition), controlling sufficient decay of slope: c₁ < 1/2 < c₂. Default is `9//10`.
  * `ϵ::Real`: Parameter for expected accuracy of objective function, controlling maximal allowed increase in function value. Default is `1//10^6`.
  * `θ::Real`: Parameter regulating the bisection step. Default is `1//2` (should probably not be changed).
  * `γ::Real`: Parameter triggering the bisection step, namely if bracket reduction rate is slower than `γ`. Default is `2//3`.
  * `ρ::Real`: Parameter controlling the initial bracket expansion rate. Default is `5//1`.

## Returns:

This method returns a `HagerZhangLineSearch` object `ls`, that can then be can be applied as `ls(fg, x₀, η₀; kwargs...)` to perform a line search for function `fg` that computes the objective function and its gradient at a given point, starting from `x₀` in direction `η₀`.
