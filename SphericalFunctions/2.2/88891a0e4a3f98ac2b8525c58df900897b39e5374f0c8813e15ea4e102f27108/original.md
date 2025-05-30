```
L²(s, ℓₘᵢₙ, ℓₘₐₓ, [T])
```

Compute the total angular-momentum operator from `ℓₘᵢₙ` up to `ℓₘₐₓ`.  If not present, `ℓₘᵢₙ` is assumed to be `abs(s)`.  The argument `s` is ignored; it is present only for consistency with other operators, and is assumed to be 0 if not present.

This is the standard $L²$ operator, familiar from basic physics, extended to work with SWSHs.  It is also known as the Casimir operator, and is equal to

$$
L^2 = L_x^2 + L_y^2 + L_z^2 = \frac{L_+L_- + L_-L_+ + 2L_zL_z}{2}.
$$

Note that these are the left Lie derivatives, but $L^2 = R^2$, where `R` is the right Lie derivative.  See [the documentation](@ref "Differential operators") or [Boyle](@cite Boyle_2016) for more details.

In terms of the SWSHs, we can write the action of $L^2$ as

$$
L^2 {}_{s}Y_{\ell,m} = \ell\,(\ell+1) {}_{s}Y_{\ell,m}
$$

See also [`Lz`](@ref), [`L₊`](@ref), [`L₋`](@ref), [`R²`](@ref), [`Rz`](@ref), [`R₊`](@ref), [`R₋`](@ref), [`ð`](@ref), [`ð̄`](@ref).
