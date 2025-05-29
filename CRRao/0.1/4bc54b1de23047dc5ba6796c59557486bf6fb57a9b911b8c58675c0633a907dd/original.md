```julia
fit(formula::FormulaTerm, data::DataFrame, modelClass::LinearRegression, prior::Prior_Gauss, alpha_prior_mean::Float64, alpha_prior_sd::Float64, beta_prior_mean::Vector{Float64}, beta_prior_sd::Vector{Float64}, sim_size::Int64 = 1000)
```

Fit a Bayesian Linear Regression model on the input data with a Gaussian prior with user specific prior mean and sd for α and β. 

# Example

```julia-repl
julia> using CRRao, RDatasets, StableRNGs, StatsModels
julia> df = dataset("datasets", "mtcars");  
julia> CRRao.set_rng(StableRNG(123));                                                                                             
julia> container = fit(@formula(MPG ~ HP + WT + Gear), df, LinearRegression(), Prior_Gauss(),30.0,10.0,[0.0,-3.0,1.0],[0.1,1.0,1.0],1000)
┌ Info: Found initial step size
└   ϵ = 0.000390625
Chains MCMC chain (1000×17×1 Array{Float64, 3}):

Iterations        = 501:1:1500
Number of chains  = 1
Samples per chain = 1000
Wall duration     = 0.4 seconds
Compute duration  = 0.4 seconds
parameters        = σ, β[1], β[2], β[3], β[4]
internals         = lp, n_steps, is_accept, acceptance_rate, log_density, hamiltonian_energy, hamiltonian_energy_error, max_hamiltonian_energy_error, tree_depth, numerical_error, step_size, nom_step_size

Summary Statistics
  parameters      mean       std   naive_se      mcse        ess      rhat   ess_per_sec 
      Symbol   Float64   Float64    Float64   Float64    Float64   Float64       Float64 

           σ    2.5902    0.3556     0.0112    0.0173   479.5282    1.0029     1207.8796
        β[1]   31.5741    3.0940     0.0978    0.1654   438.4853    1.0016     1104.4971
        β[2]   -0.0371    0.0088     0.0003    0.0003   728.7433    1.0017     1835.6254
        β[3]   -3.1311    0.5910     0.0187    0.0253   537.6704    1.0019     1354.3334
        β[4]    1.0910    0.5777     0.0183    0.0303   461.2719    1.0021     1161.8939

Quantiles
  parameters      2.5%     25.0%     50.0%     75.0%     97.5% 
      Symbol   Float64   Float64   Float64   Float64   Float64 

           σ    1.9892    2.3336    2.5579    2.8106    3.3548
        β[1]   24.9976   29.6654   31.4881   33.5860   37.6309
        β[2]   -0.0546   -0.0430   -0.0373   -0.0311   -0.0200
        β[3]   -4.2471   -3.5287   -3.1438   -2.7626   -1.9238
        β[4]   -0.0285    0.7312    1.0926    1.4948    2.1519
```
