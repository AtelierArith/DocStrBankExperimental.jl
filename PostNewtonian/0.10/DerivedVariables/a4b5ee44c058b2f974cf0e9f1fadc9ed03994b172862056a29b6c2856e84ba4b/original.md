```
λ₁(s)
```

The "quadrupolar polarisability" of object 1 used by [Marsat (2014)](https://arxiv.org/abs/1411.4118), who notes above Eq. (4.11) that this is denoted $C_{\mathrm{BS}^2}$ in [Levi and Steinhoff (2014)](https://arxiv.org/abs/1410.2601), who in turn notes that "we can set ... the Wilson coefficients $C_{\mathrm{ES}^2} = C_{\mathrm{BS}^3} = 1$ for the black hole case."

See also [`κ₁`](@ref).

!!! warn
    This function will be incorrect for objects other than black holes.  It is not clear to me if this is the same quantity as $C_Q$ used in some papers, such as [Bini and Geralico (2014)](https://arxiv.org/abs/1408.5261), but they point out that for neutron stars, the value varies between 4.3 and 7.4, depending on the equation of state.  This quantity may also be related to [`λ₁`](@ref).  Pull requests or issues with more information are welcome.

