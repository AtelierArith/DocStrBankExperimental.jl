```
Ry(alpha::T) where {T<:Number}
```

Return the rotation matrix around the y-axis

$$
R_y(\alpha) =
\left[
\begin{array}{ccc}
    \cos\alpha & 0 & -\sin\alpha \\
    0 & 1 & 0 \\
    \sin\alpha & 0 & \cos\alpha \\
\end{array}
\right],
$$

where $\alpha$ is an angle in radians.

See equation (12) in page 9 of https://ui.adsabs.harvard.edu/abs/2014IPNPR.196C...1F%2F/abstract.

$\textbf{Note:}$ Lieske et al. (1977, 1979) introduces the convention that this matrix has opposite signs outside the sine terms (with respect to `Rx`, `Rz`). See equation (4) in page 3 of https://ui.adsabs.harvard.edu/abs/1977A%26A....58....1L/abstract and equation (3) in page 283 of https://ui.adsabs.harvard.edu/abs/1979A%26A....73..282L/abstract.

See also [`Rx`](@ref) and [`Rz`](@ref).
