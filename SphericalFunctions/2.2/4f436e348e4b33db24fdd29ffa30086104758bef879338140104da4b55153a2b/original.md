```
L₋(s, ℓₘᵢₙ, ℓₘₐₓ, [T])
```

Compute the angular-momentum lowering operator.  This is the standard $L_-$ operator, familiar from basic physics, extended to work with SWSHs.  Note that this is the left Lie derivative; see [`R₋`](@ref) for the equivalent right Lie derivative.  See [the documentation](@ref "Differential operators") or [Boyle](@cite Boyle_2016) for more details.

We define $L_-$ to be the lowering operator for the left Lie derivative with respect to rotation about $z$: $L_z$.  By definition, this implies the commutator relation $[L_z, L_-] = -L_-$, which allows us to derive $L_- = L_x - i\, L_y.$

In terms of the SWSHs, we can write the action of $L_-$ as

$$
L_- {}_{s}Y_{\ell,m} = \sqrt{(\ell+m)(\ell-m+1)}\, {}_{s}Y_{\ell,m-1}.
$$

Consequently, the *mode weights* of a function are affected as

$$
\left\{L_-(f)\right\}_{s,\ell,m} = \sqrt{(\ell-m)(\ell+m+1)}\,\left\{f\right\}_{s,\ell,m+1}.
$$

See also [`L²`](@ref), [`Lz`](@ref), [`L₊`](@ref), [`L₋`](@ref), [`R²`](@ref), [`Rz`](@ref), [`R₊`](@ref), [`R₋`](@ref), [`ð`](@ref), [`ð̄`](@ref).
