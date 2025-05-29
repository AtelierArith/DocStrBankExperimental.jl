```
GlmSpeedCallback(; glm_scale=0.5, cfl, semi_indices=())
```

Update the divergence cleaning wave speed `c_h` according to the time step computed in [`StepsizeCallback`](@ref) for the ideal GLM-MHD equations, the multi-component GLM-MHD equations, and the multi-ion GLM-MHD equations. The `cfl` number should be set to the same value as for the time step size calculation.  As for standard [`StepsizeCallback`](@ref) `cfl` can be either set to a `Real` number or a function of time `t` returning a `Real` number.

The `glm_scale` ensures that the GLM wave speed is lower than the fastest physical waves in the MHD solution and should thus be set to a value within the interval [0,1]. Note that `glm_scale = 0` deactivates the divergence cleaning.

In case of coupled semidiscretizations, specify for which `semi_index`, i.e. index of the semidiscretization, the divergence cleaning should be applied. See also [`SemidiscretizationCoupled`](@ref). Note: `SemidiscretizationCoupled` and all related features are considered experimental and may change at any time.
