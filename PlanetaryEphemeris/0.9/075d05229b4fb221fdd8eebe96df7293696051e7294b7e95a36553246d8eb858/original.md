```
Rz(alpha::T) where {T<:Number}
```

Return the rotation matrix around the z-axis

$$
R_z(\alpha) =
\left[
\begin{array}{ccc}
    \cos\alpha & \sin\alpha & 0 \\
    -\sin\alpha & \cos\alpha & 0 \\
    0 & 0 & 1 \\
\end{array}
\right],
$$

where $\alpha$ is an angle in radians.

See equation (13) in page 9 of https://ui.adsabs.harvard.edu/abs/2014IPNPR.196C...1F%2F/abstract.

See also [`Rx`](@ref) and [`Ry`](@ref).
