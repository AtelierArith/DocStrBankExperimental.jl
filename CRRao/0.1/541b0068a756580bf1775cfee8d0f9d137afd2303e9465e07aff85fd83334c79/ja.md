```julia
fit(formula::FormulaTerm, data::DataFrame, modelClass::NegBinomRegression, prior::Prior_Cauchy, h::Float64 = 1.0, sim_size::Int64 = 1000)
```

入力データに対してCauchy事前分布を用いたベイズ負の二項回帰モデルを適合させます。

# 例

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
julia> container = fit(@formula(Num ~ Target + Coop + NCost), sanction, NegBinomRegression(), Prior_Cauchy())
┌ Info: Found initial step size
└   ϵ = 0.05
┌ Warning: The current proposal will be rejected due to numerical error(s).
│   isfinite.((θ, r, ℓπ, ℓκ)) = (true, false, false, false)
└ @ AdvancedHMC ~/.julia/packages/AdvancedHMC/iWHPQ/src/hamiltonian.jl:47
Chains MCMC chain (1000×19×1 Array{Float64, 3}):

Iterations        = 501:1:1500
Number of chains  = 1
Samples per chain = 1000
Wall duration     = 2.5 seconds
Compute duration  = 2.5 seconds
parameters        = λ, β[1], β[2], β[3], β[4], β[5], β[6]
internals         = lp, n_steps, is_accept, acceptance_rate, log_density, hamiltonian_energy, hamiltonian_energy_error, max_hamiltonian_energy_error, tree_depth, numerical_error, step_size, nom_step_size

Summary Statistics
  parameters      mean       std   naive_se      mcse        ess      rhat   ess_per_sec 
      Symbol   Float64   Float64    Float64   Float64    Float64   Float64       Float64 

           λ    2.0094    0.4380     0.0139    0.0169   690.8506    1.0028      276.7831
        β[1]   -1.0783    0.5492     0.0174    0.0254   373.3703    1.0000      149.5875
        β[2]   -0.0077    0.1702     0.0054    0.0075   431.5668    0.9991      172.9034
        β[3]    1.0621    0.1340     0.0042    0.0052   498.3356    0.9999      199.6537
        β[4]   -0.1812    0.5431     0.0172    0.0239   653.5156    1.0022      261.8252
        β[5]    1.2693    0.3302     0.0104    0.0128   624.9936    0.9991      250.3981
        β[6]    0.1551    0.2951     0.0093    0.0106   548.9336    1.0019      219.9253

Quantiles
  parameters      2.5%     25.0%     50.0%     75.0%     97.5% 
      Symbol   Float64   Float64   Float64   Float64   Float64 

           λ    1.3395    1.7025    1.9368    2.2640    3.0577
        β[1]   -2.2001   -1.4242   -1.0651   -0.7256   -0.0066
        β[2]   -0.3558   -0.1220   -0.0026    0.0946    0.3230
        β[3]    0.7907    0.9789    1.0606    1.1386    1.3336
        β[4]   -1.1899   -0.5662   -0.1798    0.1778    0.9467
        β[5]    0.6384    1.0495    1.2673    1.4884    1.9266
        β[6]   -0.4275   -0.0388    0.1676    0.3465    0.7206

```
