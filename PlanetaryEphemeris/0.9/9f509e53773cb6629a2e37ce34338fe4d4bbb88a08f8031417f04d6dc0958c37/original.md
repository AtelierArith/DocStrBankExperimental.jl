```
Rx(alpha::T) where {T<:Number}
```

Return the rotation matrix around the x-axis

$$
R_x(\alpha) =
\left[
\begin{array}{ccc}
    1 & 0 & 0 \\
    0 & \cos\alpha & \sin\alpha \\
    0 & -\sin\alpha & \cos\alpha \\
\end{array}
\right],
$$

where $\alpha$ is an angle in radians.

See equation (11) in page 9 of https://ui.adsabs.harvard.edu/abs/2014IPNPR.196C...1F%2F/abstract.

See also [`Ry`](@ref) and [`Rz`](@ref).
