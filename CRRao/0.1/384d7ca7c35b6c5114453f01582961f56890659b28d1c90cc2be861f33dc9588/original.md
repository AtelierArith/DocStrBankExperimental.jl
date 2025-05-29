```julia
fit(formula::FormulaTerm, data::DataFrame, modelClass::PoissonRegression, prior::Prior_TDist, h::Float64 = 2.0, sim_size::Int64 = 1000)
```

Fit a Bayesian Poisson Regression model on the input data with a t(ν) distributed prior.

# Example

```julia-repl
julia> using CRRao, RDatasets, StableRNGs, StatsModels
julia> CRRao.set_rng(StableRNG(123))
StableRNGs.LehmerRNG(state=0x000000000000000000000000000000f7)
julia> sanction = dataset("Zelig", "sanction")
78×8 DataFrame
 Row │ Mil    Coop   Target  Import  Export  Cost   Num    NCost         
     │ Int32  Int32  Int32   Int32   Int32   Int32  Int32  Cat…          
─────┼───────────────────────────────────────────────────────────────────
   1 │     1      4       3       1       1      4     15  major loss
   2 │     0      2       3       0       1      3      4  modest loss
   3 │     0      1       3       1       0      2      1  little effect
   4 │     1      1       3       1       1      2      1  little effect
  ⋮  │   ⋮      ⋮      ⋮       ⋮       ⋮       ⋮      ⋮          ⋮
  76 │     0      4       3       1       0      2     13  little effect
  77 │     0      1       2       0       0      1      1  net gain
  78 │     1      3       1       1       1      2     10  little effect
71 rows omitted
julia> CRRao.set_rng(StableRNG(123))
StableRNGs.LehmerRNG(state=0x000000000000000000000000000000f7)
julia> container = fit(@formula(Num ~ Target + Coop + NCost), sanction, PoissonRegression(), Prior_TDist())
┌ Info: Found initial step size
└   ϵ = 0.025
Chains MCMC chain (1000×20×1 Array{Float64, 3}):

Iterations        = 501:1:1500
Number of chains  = 1
Samples per chain = 1000
Wall duration     = 0.68 seconds
Compute duration  = 0.68 seconds
parameters        = λ, ν, β[1], β[2], β[3], β[4], β[5], β[6]
internals         = lp, n_steps, is_accept, acceptance_rate, log_density, hamiltonian_energy, hamiltonian_energy_error, max_hamiltonian_energy_error, tree_depth, numerical_error, step_size, nom_step_size

Summary Statistics
  parameters      mean       std   naive_se      mcse        ess      rhat   ess_per_sec 
      Symbol   Float64   Float64    Float64   Float64    Float64   Float64       Float64 

           λ    0.9539    0.3968     0.0125    0.0138   724.4593    0.9991     1071.6854
           ν    2.7018    3.4303     0.1085    0.1503   473.2383    1.0014      700.0567
        β[1]   -1.7913    0.2504     0.0079    0.0130   301.7822    0.9992      446.4233
        β[2]    0.1368    0.0650     0.0021    0.0030   512.6922    0.9998      758.4204
        β[3]    1.1322    0.0536     0.0017    0.0026   349.4069    0.9995      516.8741
        β[4]   -0.3148    0.2317     0.0073    0.0080   824.9216    0.9993     1220.2983
        β[5]    1.7001    0.1017     0.0032    0.0039   661.7511    1.0054      978.9218
        β[6]    0.3909    0.1681     0.0053    0.0068   459.0907    0.9994      679.1283

Quantiles
  parameters      2.5%     25.0%     50.0%     75.0%     97.5% 
      Symbol   Float64   Float64   Float64   Float64   Float64 

           λ    0.3999    0.6705    0.8799    1.1535    1.8898
           ν    0.5494    1.1003    1.7737    2.9372    9.8194
        β[1]   -2.2817   -1.9561   -1.7941   -1.6262   -1.2766
        β[2]    0.0151    0.0891    0.1383    0.1795    0.2614
        β[3]    1.0322    1.0932    1.1310    1.1688    1.2362
        β[4]   -0.7680   -0.4694   -0.3020   -0.1519    0.1128
        β[5]    1.5030    1.6252    1.7037    1.7682    1.8936
        β[6]    0.0701    0.2710    0.3911    0.5023    0.7236
```
