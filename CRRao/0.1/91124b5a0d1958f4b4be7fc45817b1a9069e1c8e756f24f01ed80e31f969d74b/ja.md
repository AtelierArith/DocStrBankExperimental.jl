```julia
fit(formula::FormulaTerm, data::DataFrame, modelClass::PoissonRegression, prior::Prior_Ridge, h::Float64 = 0.1, sim_size::Int64 = 1000)
```

入力データに対してリッジ事前分布を用いたベイズポアソン回帰モデルをフィットします。

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

julia> CRRao.set_rng(StableRNG(123))
StableRNGs.LehmerRNG(state=0x000000000000000000000000000000f7)
  
julia> container = fit(@formula(Num ~ Target + Coop + NCost), sanction, PoissonRegression(), Prior_Ridge())
┌ Info: Found initial step size
└   ϵ = 0.025
Chains MCMC chain (1000×19×1 Array{Float64, 3}):

Iterations        = 501:1:1500
Number of chains  = 1
Samples per chain = 1000
Wall duration     = 1.82 seconds
Compute duration  = 1.82 seconds
parameters        = λ, β[1], β[2], β[3], β[4], β[5], β[6]
internals         = lp, n_steps, is_accept, acceptance_rate, log_density, hamiltonian_energy, hamiltonian_energy_error, max_hamiltonian_energy_error, tree_depth, numerical_error, step_size, nom_step_size

Summary Statistics
  parameters      mean       std   naive_se      mcse        ess      rhat   ess_per_sec 
      Symbol   Float64   Float64    Float64   Float64    Float64   Float64       Float64 

           λ    1.3067    0.4614     0.0146    0.0187   619.3195    0.9991      339.9119
        β[1]   -1.7954    0.2642     0.0084    0.0116   469.7099    0.9999      257.7990
        β[2]    0.1387    0.0647     0.0020    0.0026   654.1981    0.9993      359.0549
        β[3]    1.1327    0.0538     0.0017    0.0017   653.9282    0.9992      358.9068
        β[4]   -0.3230    0.2179     0.0069    0.0075   743.3958    0.9994      408.0108
        β[5]    1.6961    0.0979     0.0031    0.0036   756.8072    1.0002      415.3717
        β[6]    0.4041    0.1715     0.0054    0.0068   571.0010    0.9999      313.3924

Quantiles
  parameters      2.5%     25.0%     50.0%     75.0%     97.5% 
      Symbol   Float64   Float64   Float64   Float64   Float64 

           λ    0.7431    1.0176    1.2106    1.5135    2.5469
        β[1]   -2.3068   -1.9807   -1.7939   -1.6064   -1.2936
        β[2]    0.0182    0.0939    0.1375    0.1795    0.2709
        β[3]    1.0273    1.0957    1.1309    1.1687    1.2394
        β[4]   -0.7491   -0.4674   -0.3303   -0.1709    0.1006
        β[5]    1.5116    1.6290    1.6943    1.7634    1.8955
        β[6]    0.0665    0.2867    0.4031    0.5242    0.7363

julia> predict(container,sanction)
78-element Vector{Float64}:
    17.245248953660397
    13.311751426697569
    0.7896838153702627
    0.7896838153702627
    0.7896838153702627
    0.7896838153702627
    2.12053910182601
    0.7896838153702627
    ⋮
    3.1972595300758626
    5.726972543900231
    2.7850411549518532
    0.7896838153702627
    23.451157821412178
    1.0317165509592108
    5.726972543900231
        
```
