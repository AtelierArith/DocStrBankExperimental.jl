```
simpleFWA( nFireworks::Int,
           nSparks::Int;
           λ_0::Float32,
           ϵ_A::Float32,
           C_a::Float32,
           C_r::Float32,
           lower::Vector{Float32},
           upper::Vector{Float32},
           objFunction::Function,
           XPrimary::Vector{ Matrix{Float32} },
           yPrimary::Vector{ Matrix{Float32} },
           maxiter::Int,
           ϵ_conv::Float32=1f-6 )
minimize objective function objFunction, the solution space is limited by lower and upper bound.
The optimization algorithm utilized is an simplified version of dynFireWorksAlgorithm. The nFireworks
parameter governs the number of fireworks being evaluated in parallel in each iteration.  nSparks is
the number of sparks per firework, in remains constant foreach firework. ϵ_A is the smoothing parameter
controlling the variance of amplitudes computed foreach fw. C_a ist the upscaling parameter for explosion
amplitudes. C_r is the downscaling parameter for explosion amplitudes. XPrimary is the feature set of the
primary algorithm to be tuned. yPrimary is the target set of the primary algorithm. maxiter is the maximum
number iteraions.  ϵ_conv denotes the convergence parameter.
```
