```
Lz(s, ℓₘᵢₙ, ℓₘₐₓ, [T])
```

Compute the angular-momentum operator associated with the $z$ direction.  This is the standard $L_z$ operator, familiar from basic physics, extended to work with SWSHs.  Note that this is the left Lie derivative; see [`Rz`](@ref) for the equivalent right Lie derivative.  See [the documentation](@ref "Differential operators") or [Boyle](@cite Boyle_2016) for more details.

In terms of the SWSHs, we can write the action of $L_z$ as

$$
L_z {}_{s}Y_{\ell,m} = m\, {}_{s}Y_{\ell,m}
$$

See also [`L²`](@ref), [`L₊`](@ref), [`L₋`](@ref), [`R²`](@ref), [`Rz`](@ref), [`R₊`](@ref), [`R₋`](@ref), [`ð`](@ref), [`ð̄`](@ref).
