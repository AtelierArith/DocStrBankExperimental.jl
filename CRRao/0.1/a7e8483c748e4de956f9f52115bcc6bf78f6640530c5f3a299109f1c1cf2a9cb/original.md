```julia
fit(formula::FormulaTerm, data::DataFrame, modelClass::NegBinomRegression, prior::Prior_Laplace, h::Float64 = 0.01, sim_size::Int64 = 1000)
```

Fit a Bayesian Negative Binomial Regression model on the input data with a Laplace prior.

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

julia> CRRao.set_rng(StableRNG(123))
StableRNGs.LehmerRNG(state=0x000000000000000000000000000000f7)

julia> container = fit(@formula(Num ~ Target + Coop + NCost), sanction, NegBinomRegression(), Prior_Laplace())
┌ Info: Found initial step size
└   ϵ = 0.05
Chains MCMC chain (1000×19×1 Array{Float64, 3}):

Iterations        = 501:1:1500
Number of chains  = 1
Samples per chain = 1000
Wall duration     = 2.06 seconds
Compute duration  = 2.06 seconds
parameters        = λ, β[1], β[2], β[3], β[4], β[5], β[6]
internals         = lp, n_steps, is_accept, acceptance_rate, log_density, hamiltonian_energy, hamiltonian_energy_error, max_hamiltonian_energy_error, tree_depth, numerical_error, step_size, nom_step_size

Summary Statistics
  parameters      mean       std   naive_se      mcse        ess      rhat   ess_per_sec 
      Symbol   Float64   Float64    Float64   Float64    Float64   Float64       Float64 

           λ    2.1157    0.4443     0.0141    0.0154   961.8068    0.9990      465.9917
        β[1]   -1.0085    0.5101     0.0161    0.0250   289.3129    1.0108      140.1710
        β[2]   -0.0248    0.1554     0.0049    0.0064   476.0466    1.0043      230.6427
        β[3]    1.0521    0.1305     0.0041    0.0055   342.3108    1.0075      165.8482
        β[4]   -0.1528    0.5179     0.0164    0.0183   630.1413    1.0002      305.3010
        β[5]    1.2862    0.3096     0.0098    0.0113   576.8927    1.0023      279.5023
        β[6]    0.1316    0.2634     0.0083    0.0114   491.5701    1.0014      238.1638

Quantiles
  parameters      2.5%     25.0%     50.0%     75.0%     97.5% 
      Symbol   Float64   Float64   Float64   Float64   Float64 

           λ    1.3970    1.8074    2.0635    2.3653    3.1272
        β[1]   -2.0432   -1.3326   -0.9808   -0.6653   -0.0397
        β[2]   -0.3230   -0.1281   -0.0271    0.0741    0.2848
        β[3]    0.8077    0.9677    1.0496    1.1381    1.3186
        β[4]   -1.1888   -0.4738   -0.1480    0.1743    0.8940
        β[5]    0.6787    1.0819    1.3003    1.4830    1.8838
        β[6]   -0.3786   -0.0462    0.1339    0.3186    0.6422
        
julia> predict(container,sanction)
78-element Vector{Float64}:
21.842690660989987
10.491546187713833
1.0011451666062938
1.0011451666062938
1.0011451666062938
1.0011451666062938
2.890144338154678
1.0011451666062938
⋮
3.29313752935312
8.611185000528977
3.4080264307792745
1.0011451666062938
23.744012407689187
1.1547110091441486
8.611185000528977
```
