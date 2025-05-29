```
ITM2(ωx::T, ωy::T, ωz::T) where {T <: Number}
```

Return the second term of the time-dependent part of lunar total moment of intertia

$$
\frac{k_{2,M} R_M^5}{3G}
\left[
\begin{array}{ccc}
    \omega_{m,x}^2 - \frac{1}{3}(\omega_m^2 - n^2) & \omega_{m,x}\omega_{m,y} & \omega_{m,x}\omega_{m,z} \\
    \omega_{m,x}\omega_{m,y} & \omega_{m,y}^2 - \frac{1}{3}(\omega_m^2 - n^2) & \omega_{m,y}\omega_{m,z} \\
    \omega_{m,x}\omega_{m,z} & \omega_{m,y}\omega_{m,z} & \omega_{m,z}^2 - \frac{1}{3}(\omega_m^2 + 2n^2) \\
\end{array}
\right],
$$

where $\mathbf{\omega}_m = (\omega_{m,x}, \omega_{m,y}, \omega_{m,z})$ is the angular velocity of the mantle in the mantle frame, $k_{2,M}$ is the lunar potential Love number, $R_M$ is the equatorial radius of the Moon and $n$ is the lunar mean motion.

$\textbf{Note:}$ Euler angles must be evaluated at time $t-τ_M$.

See the second term of equation (41) in page 17 of https://ui.adsabs.harvard.edu/abs/2014IPNPR.196C...1F%2F/abstract.

See also [`ITM1`](@ref) and [`ITM`](@ref).
