```
c2t_jpl_de430(t)
```

Return the matrix for celestial-to-terrestrial coordinate transformation, according to JPL DE 430/431 Earth orientation model

$$
\texttt{c2t_jpl_de430}(t) = A\times C\times N,
$$

where $t$ is the TDB time in Julian days from J2000.0, $A = R_z(-z_A(t))R_y(\theta_A(t))R_z(-\zeta_A(t))$ is the precession matrix, $C = R_y(\phi_y(t))R_x(\phi_x(t))$ is the linear corrections matrix and $N$ is the nutation matrix.

See equation (5-147) in page (5-59) and equation (5-152) in page (5-60) of https://doi.org/10.1002/0471728470. Also see equation (25) in page 11 and Table 10 in page 50 of https://ui.adsabs.harvard.edu/abs/2014IPNPR.196C...1F%2F/abstract.

See also [`Rx`](@ref), [`Ry`](@ref), [`Rz`](@ref) and [`nutation_iau80`](@ref).
