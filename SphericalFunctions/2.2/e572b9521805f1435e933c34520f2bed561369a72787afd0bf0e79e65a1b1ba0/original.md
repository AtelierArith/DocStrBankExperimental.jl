```
R₋(s, ℓₘᵢₙ, ℓₘₐₓ, [T])
```

Compute the *right* angular-momentum lowering operator.

This is the $R_-$ operator, much like the $L_-$ operator familiar from basic physics, but in terms of the right Lie derivative, and extended to work with SWSHs.  See [`L₋`](@ref) for the equivalent left Lie derivative.  See [the documentation](@ref "Differential operators") or [Boyle](@cite Boyle_2016) for more details.

We define $R_-$ to be the raising operator for the right Lie derivative with respect to rotation about $z$: $R_z$.  By definition, this implies the commutator relation $[R_z, R_-] = -R_-$, which allows us to derive $R_- = R_x + i\, R_y.$

In terms of the SWSHs, we can write the action of $R_-$ as

$$
R_- {}_{s}Y_{\ell,m} = \sqrt{(\ell-s)(\ell+s+1)}\, {}_{s+1}Y_{\ell,m}
$$

Consequently, the *mode weights* of a function are affected as

$$
\left\{R_-(f)\right\}_{s,\ell,m} = \sqrt{(\ell-s)(\ell+s+1)}\,\left\{f\right\}_{s+1,\ell,m}.
$$

Because of the unfortunate sign of $s$ arising from the choice of definition of $s$ in the original paper by [Newman and Penrose](@cite Newman_1966), this is a *raising* operator for $s$, though it really is a *lowering* operator for $R_z$, and lowers the eigenvalue of the corresponding Wigner matrix - though that raises the eigenvalue of the corresponding Wigner matrix.

See also [`L²`](@ref), [`Lz`](@ref), [`L₊`](@ref), [`L₋`](@ref), [`R²`](@ref), [`Rz`](@ref), [`R₊`](@ref), [`ð`](@ref), [`ð̄`](@ref).
