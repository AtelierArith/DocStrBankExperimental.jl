```
spin_coherent(j::Real, θ::Real, ϕ::Real)
```

Generate the coherent spin state (rotation of the $|j, j\rangle$ state), namely

$$
|\theta, \phi \rangle = \hat{R}(\theta, \phi) |j, j\rangle
$$

where the rotation operator is defined as

$$
\hat{R}(\theta, \phi) = \exp \left( \frac{\theta}{2} (\hat{S}_- e^{i\phi} - \hat{S}_+ e^{-i\phi}) \right)
$$

and $\hat{S}_\pm$ are plus and minus Spin-`j` operators, respectively.

# Arguments

  * `j::Real`: The spin quantum number and can be a non-negative integer or half-integer
  * `θ::Real`: rotation angle from z-axis
  * `ϕ::Real`: rotation angle from x-axis

See also [`jmat`](@ref) and [`spin_state`](@ref).

# Reference

  * [Robert Jones, Spin Coherent States and Statistical Physics](https://web.mit.edu/8.334/www/grades/projects/projects19/JonesRobert.pdf)
