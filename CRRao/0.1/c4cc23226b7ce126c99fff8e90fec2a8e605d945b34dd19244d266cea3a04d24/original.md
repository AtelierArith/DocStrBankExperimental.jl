```julia
fit(formula::FormulaTerm, data::DataFrame, modelClass::NegBinomRegression, prior::Prior_TDist, h::Float64 = 1.0, sim_size::Int64 = 1000)
```

Fit a Bayesian Negative Binomial Regression model on the input data with a t(ν) distributed prior.

# Example

```julia-repl
julia> using CRRao, RDatasets, StableRNGs, StatsModels
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
julia> container = fit(@formula(Num ~ Target + Coop + NCost), sanction, NegBinomRegression(), Prior_TDist())
┌ Info: Found initial step size
└   ϵ = 0.05
Chains MCMC chain (1000×20×1 Array{Float64, 3}):

Iterations        = 501:1:1500
Number of chains  = 1
Samples per chain = 1000
Wall duration     = 2.71 seconds
Compute duration  = 2.71 seconds
parameters        = λ, ν, β[1], β[2], β[3], β[4], β[5], β[6]
internals         = lp, n_steps, is_accept, acceptance_rate, log_density, hamiltonian_energy, hamiltonian_energy_error, max_hamiltonian_energy_error, tree_depth, numerical_error, step_size, nom_step_size

Summary Statistics
  parameters      mean        std   naive_se      mcse        ess      rhat   ess_per_sec 
      Symbol   Float64    Float64    Float64   Float64    Float64   Float64       Float64 

           λ    2.0088     0.4446     0.0141    0.0161   819.9421    0.9990      302.1157
           ν   21.7233   116.4227     3.6816    4.9619   685.3526    0.9996      252.5249
        β[1]   -1.0604     0.5311     0.0168    0.0283   397.1943    0.9997      146.3502
        β[2]   -0.0109     0.1620     0.0051    0.0068   654.7909    1.0005      241.2642
        β[3]    1.0601     0.1326     0.0042    0.0071   449.7489    0.9992      165.7144
        β[4]   -0.1635     0.5340     0.0169    0.0187   724.3698    0.9996      266.9012
        β[5]    1.2760     0.3239     0.0102    0.0119   679.5304    1.0006      250.3797
        β[6]    0.1456     0.2862     0.0091    0.0133   500.7724    0.9991      184.5145

Quantiles
  parameters      2.5%     25.0%     50.0%     75.0%      97.5% 
      Symbol   Float64   Float64   Float64   Float64    Float64 

           λ    1.2838    1.6993    1.9651    2.2594     3.0105
           ν    0.7203    1.9770    4.0830   10.1954   152.7865
        β[1]   -2.1498   -1.4146   -1.0534   -0.6976    -0.0150
        β[2]   -0.3198   -0.1253   -0.0024    0.1027     0.3046
        β[3]    0.8080    0.9688    1.0538    1.1519     1.3261
        β[4]   -1.2265   -0.5194   -0.1622    0.2064     0.8424
        β[5]    0.6213    1.0451    1.2792    1.4909     1.8955
        β[6]   -0.4084   -0.0453    0.1477    0.3433     0.7080

```
