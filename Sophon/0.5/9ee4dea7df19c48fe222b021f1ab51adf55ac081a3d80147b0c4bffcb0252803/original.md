```
QuasiRandomSampler(pde_points, bcs_points=pde_points;
                   sampling_alg=SobolSample(),
                   resample = false))
```

Sampler to generate the datasets for PDE and boundary conditions using a quisa-random sampling algorithm. You can call `sample(pde, sampler, strategy)` on it to generate all the datasets. See [QuasiMonteCarlo.jl](https://github.com/SciML/QuasiMonteCarlo.jl) for available sampling algorithms. The default element type of the sampled data is `Float64`. The initial sampled data lives on GPU if [`PINN`](@ref) is. You will need manually move the data to GPU if you want to resample.

## Arguments

  * `pde_points`: The number of points to sample for each PDE. If a single number is given, the same number of points will be sampled for each PDE. If a tuple of numbers is given, the number of points for each PDE will be the corresponding element in the tuple. The default is `100`.
  * `bcs_points`: The number of points to sample for each boundary condition. If a single number is given, the same number of points will be sampled for each boundary condition. If a tuple of numbers is given, the number of points for each boundary condition will be the corresponding element in the tuple. The default is `pde_points`.

## Keyword Arguments

  * `sampling_alg`: The sampling algorithm to use. The default is `SobolSample()`.
  * `resample`: Whether to resample the data for each equation. The default is `false`, which can save a lot of memory if you are solving a large number of PDEs. In this case, `pde_points` has to be a integer. If you want to resample the data, you will need to manually move the data to GPU if you want to use GPU to solve the PDEs.
