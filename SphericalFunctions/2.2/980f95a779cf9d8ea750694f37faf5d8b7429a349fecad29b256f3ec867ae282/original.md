```
R²(s, ℓₘᵢₙ, ℓₘₐₓ, [T])
```

Compute the total angular-momentum operator from `ℓₘᵢₙ` up to `ℓₘₐₓ`.  If not present, `ℓₘᵢₙ` is assumed to be `abs(s)`.  The argument `s` is ignored; it is present only for consistency with other operators, and is assumed to be 0 if not present.

This is the $R^2$ operator, much like the $L^2$ operator familiar from basic physics, but in terms of the right Lie derivative, and extended to work with SWSHs.  It is also known as the Casimir operator, and is equal to

$$
R^2 = R_x^2 + R_y^2 + R_z^2 = \frac{R_+R_- + R_-R_+ + 2R_zR_z}{2}.
$$

Note that these are the right Lie derivatives, but $L^2 = R^2$, where `L` is the left Lie derivative.  See [the documentation](@ref "Differential operators") or [Boyle](@cite Boyle_2016) for more details.

In terms of the SWSHs, we can write the action of $R^2$ as

$$
R^2 {}_{s}Y_{\ell,m} = \ell\,(\ell+1) {}_{s}Y_{\ell,m}
$$

See also [`L²`](@ref), [`Lz`](@ref), [`L₊`](@ref), [`L₋`](@ref), [`Rz`](@ref), [`R₊`](@ref), [`R₋`](@ref), [`ð`](@ref), [`ð̄`](@ref).
