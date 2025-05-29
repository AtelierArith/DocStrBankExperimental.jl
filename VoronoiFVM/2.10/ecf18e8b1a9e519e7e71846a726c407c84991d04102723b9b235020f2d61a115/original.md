```julia
fbernoulli_pm(x)

```

Bernoulli function $B(x)=\frac{x}{e^x-1}$ for exponentially fitted upwind, joint evaluation for positive and negative argument

Usually, we need $B(x), B(-x)$ together,  and it is cheaper to calculate them together.

Returns two real numbers containing the result for argument `x` and argument `-x`. 

For the general approach to the implementation, see the discussion in [`fbernoulli`](@ref).
