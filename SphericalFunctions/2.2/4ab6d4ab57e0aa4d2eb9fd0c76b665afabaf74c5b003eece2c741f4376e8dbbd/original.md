```
ð(s, ℓₘᵢₙ, ℓₘₐₓ, [T])
```

Compute coefficients for the spin-raising operator $\eth$.

This operator was originally defined by [Newman and Penrose](@cite Newman_1966), but is more completely defined by [Boyle](@cite Boyle_2016).  It is identical to [`R₋`](@ref).  Refer to that function's documentation for more details.

By definition, the spin-raising operator satisfies the commutator relation $[S, \eth] = \eth$ (where $S$ is the spin operator, which just multiplies the function by its spin). In terms of the SWSHs, we can write the action of $\eth$ as

$$
    \eth {}_{s}Y_{\ell,m} = \sqrt{(\ell-s)(\ell+s+1)} {}_{s+1}Y_{\ell,m}.
$$

Consequently, the *mode weights* of a function are affected as

$$
\left\{\eth f\right\}_{s,\ell,m} = \sqrt{(\ell-s)(\ell+s+1)}\,\left\{f\right\}_{s+1,\ell,m}.
$$

See also [`ð̄`](@ref),  [`L²`](@ref), [`Lz`](@ref), [`L₊`](@ref), [`L₋`](@ref), [`R²`](@ref), [`Rz`](@ref), [`R₊`](@ref).
