```
AbstractShallowWaterEquations{NDIMS, NVARS}
```

An abstract supertype of all equation system that contain the classical shallow water equations as a subsystem, e.g., the [`BBMBBMEquations1D`](@ref), the [`SvaerdKalischEquations1D`](@ref), and the [`SerreGreenNaghdiEquations1D`](@ref). In 1D, the shallow water equations with flat bathymetry are given by

$$
\begin{aligned}
  h_t + (h v)_x &= 0,\\
  h v_t + \frac{1}{2} g (h^2)_x + \frac{1}{2} h (v^2)_x &= 0,
\end{aligned}
$$

where $h$ is the [`waterheight`](@ref), $v$ the [`velocity`](@ref), and $g$ the [`gravity`](@ref).
