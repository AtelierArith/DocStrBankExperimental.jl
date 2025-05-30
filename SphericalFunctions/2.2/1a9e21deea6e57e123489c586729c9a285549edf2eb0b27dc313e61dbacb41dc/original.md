```
Rz(s, ℓₘᵢₙ, ℓₘₐₓ, [T])
```

Compute the *right* angular-momentum operator associated with the $z$ direction.

This is the $R_z$ operator, much like the $L_z$ operator familiar from basic physics, but in terms of the right Lie derivative, and extended to work with SWSHs.  See [`Lz`](@ref) for the equivalent left Lie derivative.  See [the documentation](@ref "Differential operators") or [Boyle](@cite Boyle_2016) for more details.

In terms of the SWSHs, we can write the action of $R_z$ as

$$
R_z {}_{s}Y_{\ell,m} = -s\, {}_{s}Y_{\ell,m}
$$

Note the unfortunate sign of $s$, which seems to be opposite to what we expect, and arises from the choice of definition of $s$ in the original paper by [Newman and Penrose](@cite Newman_1966).

See also [`L²`](@ref), [`Lz`](@ref), [`L₊`](@ref), [`L₋`](@ref), [`R²`](@ref), [`R₊`](@ref), [`R₋`](@ref), [`ð`](@ref), [`ð̄`](@ref).
