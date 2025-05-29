```julia
fit(formula::FormulaTerm, data::DataFrame, modelClass::NegBinomRegression, prior::Prior_Ridge, h::Float64 = 1.0, sim_size::Int64 = 1000)
```

Fit a Bayesian Negative Binomial Regression model on the input data with a Ridge prior.

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
  
julia> container = fit(@formula(Num ~ Target + Coop + NCost), sanction, NegBinomRegression(), Prior_Ridge())
┌ Info: Found initial step size
└   ϵ = 0.05
Chains MCMC chain (1000×19×1 Array{Float64, 3}):

Iterations        = 501:1:1500
Number of chains  = 1
Samples per chain = 1000
Wall duration     = 2.1 seconds
Compute duration  = 2.1 seconds
parameters        = λ, β[1], β[2], β[3], β[4], β[5], β[6]
internals         = lp, n_steps, is_accept, acceptance_rate, log_density, hamiltonian_energy, hamiltonian_energy_error, max_hamiltonian_energy_error, tree_depth, numerical_error, step_size, nom_step_size

Summary Statistics
  parameters      mean       std   naive_se      mcse        ess      rhat   ess_per_sec 
      Symbol   Float64   Float64    Float64   Float64    Float64   Float64       Float64 

           λ    2.0335    0.4164     0.0132    0.0144   602.6989    1.0028      287.2731
        β[1]   -1.1009    0.5388     0.0170    0.0349   216.8922    0.9992      103.3804
        β[2]    0.0011    0.1636     0.0052    0.0095   304.5594    0.9995      145.1665
        β[3]    1.0603    0.1306     0.0041    0.0074   370.3104    0.9994      176.5064
        β[4]   -0.1579    0.5449     0.0172    0.0214   884.5495    1.0033      421.6156
        β[5]    1.2946    0.3216     0.0102    0.0120   734.1990    1.0016      349.9519
        β[6]    0.1590    0.2913     0.0092    0.0143   426.8561    0.9990      203.4586

Quantiles
  parameters      2.5%     25.0%     50.0%     75.0%     97.5% 
      Symbol   Float64   Float64   Float64   Float64   Float64 

           λ    1.3742    1.7265    2.0057    2.2686    2.9704
        β[1]   -2.1760   -1.4541   -1.0944   -0.7251   -0.0849
        β[2]   -0.3026   -0.1087   -0.0005    0.1103    0.3231
        β[3]    0.7923    0.9728    1.0539    1.1497    1.3159
        β[4]   -1.1527   -0.5150   -0.1671    0.1970    1.0099
        β[5]    0.6724    1.0801    1.2830    1.5037    1.9353
        β[6]   -0.4259   -0.0374    0.1497    0.3484    0.7325

julia> predict(container,sanction)
78-element Vector{Float64}:
22.79273367298059
10.581746802932752
0.9868233460913254
0.9868233460913254
0.9868233460913254
0.9868233460913254
2.7991113722871277
0.9868233460913254
⋮
3.3444210972984827
8.219200484970807
3.3499195503093064
0.9868233460913254
24.39047761169405
1.1542620442281972
8.219200484970807
```
