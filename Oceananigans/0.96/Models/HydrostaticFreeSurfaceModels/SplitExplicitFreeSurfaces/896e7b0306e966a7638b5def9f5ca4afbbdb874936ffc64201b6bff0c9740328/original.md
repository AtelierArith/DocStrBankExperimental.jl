```
SplitExplicitFreeSurface(grid = nothing;
                         gravitational_acceleration = g_Earth,
                         substeps = nothing,
                         cfl = nothing,
                         fixed_Δt = nothing,
                         averaging_kernel = averaging_shape_function,
                         timestepper = ForwardBackwardScheme())
```

Return a `SplitExplicitFreeSurface` representing an explicit time discretization of a free surface dynamics with `gravitational_acceleration`. The free surface dynamics are solved by discretizing:

$$
\begin{gather}
∂_t η = - \nabla ⋅ U, \\
∂_t U = - g H \nabla η + G^U,
\end{gather}
$$

where $η$ is the free surface displacement, $U$ is the barotropic velocity vector, calculated as the vertical integral of the velocity field $u$ and $v$, $H$ is the column depth, $G^U$ is the slow forcing calculated as the integral of the tendency of $u$ and $v$, and $g$ is the gravitational acceleration.

The discretized equations are solved within a baroclinic timestep ($Δt$) by substepping with a $Δτ < Δt$. The barotropic velocities are filtered throughout the substepping and, finally, the barotropic mode of the velocities at the new time step is corrected with the filtered velocities.

# Keyword Arguments

  * `gravitational_acceleration`: the gravitational acceleration (default: `g_Earth`)
  * `substeps`: The number of substeps that divide the range `(t, t + 2Δt)`, where `Δt` is the baroclinic             timestep. Note that some averaging functions do not require substepping until `2Δt`.             The number of substeps is reduced automatically to the last index of `averaging_kernel`             for which `averaging_kernel > 0`.
  * `cfl`: If set then the number of `substeps` are computed based on the advective timescale imposed from        the barotropic gravity-wave speed that corresponds to depth `grid.Lz`. If `fixed_Δt` is provided,        then the number of `substeps` adapts to maintain an exact `cfl`. If not, the effective cfl will        always be lower than the specified `cfl` provided that the baroclinic time step satisfies        `Δt_baroclinic < fixed_Δt`.

!!! info "Needed keyword arguments"
    Either `substeps` *or* `cfl` need to be prescribed.

    When `cfl` is prescribed then `grid` is also required as a positional argument.


  * `fixed_Δt`: The maximum baroclinic timestep allowed. If `fixed_Δt` is a `nothing` and a cfl is provided,             then the number of substeps will be computed on the fly from the baroclinic time step to             maintain a constant cfl.
  * `averaging_kernel`: A function of `τ` used to average the barotropic transport `U` and the free surface                     `η` within the barotropic advancement. `τ` is the fractional substep going from 0 to 2                     with the baroclinic time step `t + Δt` located at `τ = 1`. The `averaging_kernel`                     function should be centered at `τ = 1`, that is, $∑ (aₘ m / M) = 1$, where the                     the summation occurs for $m = 1, ..., M_*$. Here, $m = 0$ and $m = M$ correspond                     to the two consecutive baroclinic timesteps between which the barotropic timestepping                     occurs and $M_*$ corresponds to the last barotropic time step for which the                     `averaging_kernel > 0`. By default, the averaging kernel described by [Shchepetkin2005](@citet)                     is used.
  * `timestepper`: Time stepping scheme used for the barotropic advancement. Choose one of:

      * `ForwardBackwardScheme()` (default): `η = f(U)`   then `U = f(η)`,
      * `AdamsBashforth3Scheme()`: `η = f(U, Uᵐ⁻¹, Uᵐ⁻²)` then `U = f(η, ηᵐ, ηᵐ⁻¹, ηᵐ⁻²)`.

# References

Shchepetkin, A. F., & McWilliams, J. C. (2005). The regional oceanic modeling system (ROMS): a split-explicit, free-surface, topography-following-coordinate oceanic model. Ocean Modelling, 9(4), 347-404.
