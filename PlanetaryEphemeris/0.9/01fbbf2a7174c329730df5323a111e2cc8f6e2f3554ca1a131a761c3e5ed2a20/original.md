```
ITM1(x::T, y::T, z::T) where {T <: Number}
```

Return the first term of the time-dependent part of lunar total moment of intertia

$$
-\frac{k_{2,M} m_E R_M^5}{r^5}
\left[
\begin{array}{ccc}
    x^2 - \frac{1}{3}r^2 & xy & xz \\
    xy & y^2 - \frac{1}{3}r^2 & yz \\
    xz & yz & z^2 - \frac{1}{3}r^2 \\
\end{array}
\right],
$$

where $\mathbf{r} = (x, y, z)$ is the position of the Moon relative to Earth referred to the mantle frame, $k_{2,M}$ is the lunar potential Love number, $m_E$ is the mass of the Earth and $R_M$ is the equatorial radius of the Moon.

See the first term of equation (41) in page 17 of https://ui.adsabs.harvard.edu/abs/2014IPNPR.196C...1F%2F/abstract.

See also [`ITM2`](@ref) and [`ITM`](@ref).
