```julia
fit(formula::FormulaTerm, data::DataFrame, modelClass::PoissonRegression, prior::Prior_Laplace, h::Float64 = 0.1, sim_size::Int64 = 1000)
```

入力データに対してラプラス事前分布を用いたベイズポアソン回帰モデルをフィットします。

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
julia> container = fit(@formula(Num ~ Target + Coop + NCost), sanction, PoissonRegression(), Prior_Laplace())
┌ Info: Found initial step size
└   ϵ = 0.025
Chains MCMC chain (1000×19×1 Array{Float64, 3}):

Iterations        = 501:1:1500
Number of chains  = 1
Samples per chain = 1000
Wall duration     = 1.83 seconds
Compute duration  = 1.83 seconds
parameters        = λ, β[1], β[2], β[3], β[4], β[5], β[6]
internals         = lp, n_steps, is_accept, acceptance_rate, log_density, hamiltonian_energy, hamiltonian_energy_error, max_hamiltonian_energy_error, tree_depth, numerical_error, step_size, nom_step_size

Summary Statistics
  parameters      mean       std   naive_se      mcse        ess      rhat   ess_per_sec 
      Symbol   Float64   Float64    Float64   Float64    Float64   Float64       Float64 

           λ    1.0888    0.5555     0.0176    0.0299   479.8254    1.0001      262.4865
        β[1]   -1.7821    0.2695     0.0085    0.0134   462.2693    0.9996      252.8826
        β[2]    0.1346    0.0613     0.0019    0.0025   677.6548    0.9992      370.7083
        β[3]    1.1312    0.0573     0.0018    0.0025   539.8120    0.9993      295.3020
        β[4]   -0.3032    0.2243     0.0071    0.0080   665.6348    1.0004      364.1328
        β[5]    1.6986    0.0987     0.0031    0.0036   701.9177    0.9991      383.9812
        β[6]    0.3837    0.1743     0.0055    0.0069   605.4188    1.0001      331.1919

Quantiles
  parameters      2.5%     25.0%     50.0%     75.0%     97.5% 
      Symbol   Float64   Float64   Float64   Float64   Float64 

           λ    0.4487    0.7271    0.9567    1.2873    2.4804
        β[1]   -2.3044   -1.9714   -1.7767   -1.5968   -1.2912
        β[2]    0.0216    0.0939    0.1302    0.1750    0.2612
        β[3]    1.0107    1.0931    1.1321    1.1708    1.2404
        β[4]   -0.7412   -0.4491   -0.2980   -0.1489    0.1149
        β[5]    1.5122    1.6303    1.6944    1.7690    1.8982
        β[6]    0.0486    0.2672    0.3897    0.4973    0.7221
julia> predict(container,sanction)
78-element Vector{Float64}:
    17.600829854957034
    13.353816665957497
    0.7892315194893381
    0.7892315194893381
    0.7892315194893381
    0.7892315194893381
    2.1250050292583618
    0.7892315194893381
    ⋮
    3.149014396126593
    5.759286021571133
    2.7567571295421613
    0.7892315194893381
    23.288584913402246
    1.0177004055294072
    5.759286021571133
```
