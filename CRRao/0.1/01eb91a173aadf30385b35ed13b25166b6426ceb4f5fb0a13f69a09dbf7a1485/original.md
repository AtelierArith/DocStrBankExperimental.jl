```julia
fit(formula::FormulaTerm, data::DataFrame, modelClass::LinearRegression, prior::Prior_Gauss,alpha_prior_mean::Float64 = 0.0, beta_prior_mean::Float64, sim_size::Int64 = 1000, h::Float64 = 0.1)
```

Fit a Bayesian Linear Regression model on the input data with a Gaussian prior with user specific prior mean for α and β. User doesnot have     idea about the prior sd of α and β. User ignore the specification for sd of α and β.

# Example

```julia-repl
julia> using CRRao, RDatasets, StableRNGs, StatsModels
julia> df = dataset("datasets", "mtcars");
julia> CRRao.set_rng(StableRNG(123));
julia> container = fit(@formula(MPG ~ HP + WT + Gear), df, LinearRegression(), Prior_Gauss(),30.0,[0.0,-3.0,1.0],1000)
┌ Info: Found initial step size
└   ϵ = 0.000390625
Chains MCMC chain (1000×17×1 Array{Float64, 3}):

Iterations        = 501:1:1500
Number of chains  = 1
Samples per chain = 1000
Wall duration     = 0.44 seconds
Compute duration  = 0.44 seconds
parameters        = σ, β[1], β[2], β[3], β[4]
internals         = lp, n_steps, is_accept, acceptance_rate, log_density, hamiltonian_energy, hamiltonian_energy_error, max_hamiltonian_energy_error, tree_depth, numerical_error, step_size, nom_step_size

Summary Statistics
  parameters      mean       std   naive_se      mcse        ess      rhat   ess_per_sec 
      Symbol   Float64   Float64    Float64   Float64    Float64   Float64       Float64 

           σ    2.4817    0.3419     0.0108    0.0164   442.9220    1.0038     1011.2375
        β[1]   30.6898    2.2222     0.0703    0.1024   277.8914    1.0096      634.4553
        β[2]   -0.0383    0.0089     0.0003    0.0004   558.2894    1.0000     1274.6332
        β[3]   -2.9652    0.5603     0.0177    0.0242   417.3633    1.0013      952.8843
        β[4]    1.2305    0.4641     0.0147    0.0214   312.8441    1.0115      714.2558

Quantiles
  parameters      2.5%     25.0%     50.0%     75.0%     97.5% 
      Symbol   Float64   Float64   Float64   Float64   Float64 

           σ    1.8921    2.2422    2.4544    2.6939    3.2290
        β[1]   26.4166   29.1803   30.7420   32.1294   34.8860
        β[2]   -0.0552   -0.0442   -0.0380   -0.0323   -0.0214
        β[3]   -4.0735   -3.3125   -2.9765   -2.6029   -1.8782
        β[4]    0.3809    0.8875    1.2182    1.5413    2.1436
```
