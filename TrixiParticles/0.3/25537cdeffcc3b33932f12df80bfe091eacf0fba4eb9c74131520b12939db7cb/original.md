```
ParticlePackingSystem(shape::InitialCondition;
                      signed_distance_field::SignedDistanceField,
                      smoothing_kernel=SchoenbergQuinticSplineKernel{ndims(shape)}(),
                      smoothing_length=shape.particle_spacing,
                      smoothing_length_interpolation=smoothing_length,
                      is_boundary=false, boundary_compress_factor=1,
                      neighborhood_search=GridNeighborhoodSearch{ndims(shape)}(),
                      background_pressure, tlsph=true, fixed_system=false)
```

System to generate body-fitted particles for complex shapes. For more information on the methods, see description below.

# Arguments

  * `shape`: [`InitialCondition`](@ref) to be packed.

# Keywords

  * `background_pressure`:   Constant background pressure to physically pack the particles.                          A large `background_pressure` can cause high accelerations                          which requires a properly adjusted time step.
  * `tlsph`:                 With the [`TotalLagrangianSPHSystem`](@ref), particles need to be placed                          on the boundary of the shape and not half a particle spacing away,                          as for fluids. When `tlsph=true`, particles will be placed                          on the boundary of the shape.
  * `is_boundary`:           When `shape` is inside the geometry that was used to create                          `signed_distance_field, set`is*boundary=false`.                          Otherwise (`shape`is the sampled boundary), set`is*boundary=true`.                          The thickness of the boundary is specified by creating`signed*distance*field`with:                             -`use*for*boundary*packing=true`-`max*signed*distance=boundary*thickness`See [`SignedDistanceField`](@ref).
  * `fixed_system`:          When set to `true`, the system remains static, meaning particles                          will not move and the `InitialCondition` will stay unchanged.                          This is useful when the system is packed together with another                          (non-fixed) `ParticlePackingSystem`.                          In this case, no `SignedDistanceField` is required for both                          the fixed and non-fixed system (use `nothing` as signed distance field).
  * `signed_distance_field`: To constrain particles onto the surface, the information about                          the signed distance from a particle to a face is required.                          The precalculated signed distances will be interpolated                          to each particle during the packing procedure.
  * `smoothing_kernel`:      Smoothing kernel to be used for this system.                          See [Smoothing Kernels](@ref smoothing_kernel).
  * `smoothing_length`:      Smoothing length to be used for the gradient estimation.                          See [Smoothing Kernels](@ref smoothing_kernel).
  * `smoothing_length_interpolation`: Smoothing length to be used for interpolating the `SignedDistanceField` information.                                   The default is `smoothing_length_interpolation = smoothing_length`.
