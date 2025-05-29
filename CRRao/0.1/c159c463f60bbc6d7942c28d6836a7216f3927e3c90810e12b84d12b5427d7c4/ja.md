```julia
fit(formula::FormulaTerm, data::DataFrame, modelClass::LinearRegression, prior::Prior_TDist, h::Float64 = 2.0, sim_size::Int64 = 1000)
```

t(ν)分布の事前分布を持つベイズ線形回帰モデルを入力データにフィットさせます。

# 例

```julia-repl
julia> using CRRao, RDatasets, StableRNGs, StatsPlots, StatsModels
julia> df = dataset("datasets", "mtcars")
32×12 DataFrame
 Row │ Model              MPG      Cyl    Disp     HP     DRat     WT       QSec     VS     AM     Gear   Carb  
     │ String31           Float64  Int64  Float64  Int64  Float64  Float64  Float64  Int64  Int64  Int64  Int64 
─────┼──────────────────────────────────────────────────────────────────────────────────────────────────────────
   1 │ Mazda RX4             21.0      6    160.0    110     3.9     2.62     16.46      0      1      4      4
   2 │ Mazda RX4 Wag         21.0      6    160.0    110     3.9     2.875    17.02      0      1      4      4
   3 │ Datsun 710            22.8      4    108.0     93     3.85    2.32     18.61      1      1      4      1
   4 │ Hornet 4 Drive        21.4      6    258.0    110     3.08    3.215    19.44      1      0      3      1
  ⋮  │         ⋮             ⋮       ⋮       ⋮       ⋮       ⋮        ⋮        ⋮       ⋮      ⋮      ⋮      ⋮
  30 │ Ferrari Dino          19.7      6    145.0    175     3.62    2.77     15.5       0      1      5      6
  31 │ Maserati Bora         15.0      8    301.0    335     3.54    3.57     14.6       0      1      5      8
  32 │ Volvo 142E            21.4      4    121.0    109     4.11    2.78     18.6       1      1      4      2
julia> CRRao.set_rng(StableRNG(123))
StableRNGs.LehmerRNG(state=0x000000000000000000000000000000f7)

julia> container = fit(@formula(MPG ~ HP + WT + Gear), df, LinearRegression(), Prior_TDist())
┌ Info: Found initial step size
└   ϵ = 2.44140625e-5
Chains MCMC chain (1000×18×1 Array{Float64, 3}):

Iterations        = 501:1:1500
Number of chains  = 1
Samples per chain = 1000
Wall duration     = 3.08 seconds
Compute duration  = 3.08 seconds
parameters        = ν, σ, β[1], β[2], β[3], β[4]
internals         = lp, n_steps, is_accept, acceptance_rate, log_density, hamiltonian_energy, hamiltonian_energy_error, max_hamiltonian_energy_error, tree_depth, numerical_error, step_size, nom_step_size

Summary Statistics
  parameters      mean       std   naive_se      mcse        ess      rhat   ess_per_sec 
      Symbol   Float64   Float64    Float64   Float64    Float64   Float64       Float64 

           ν    1.0756    0.5583     0.0177    0.0260   513.4511    0.9990      166.7049
           σ    2.6164    0.3540     0.0112    0.0178   417.8954    0.9990      135.6803
        β[1]   29.9375    4.8157     0.1523    0.2756   247.5134    1.0049       80.3615
        β[2]   -0.0396    0.0096     0.0003    0.0004   416.4579    0.9996      135.2136
        β[3]   -2.7843    0.8477     0.0268    0.0424   271.7779    1.0003       88.2396
        β[4]    1.3307    0.8752     0.0277    0.0477   275.8558    1.0047       89.5636

Quantiles
  parameters      2.5%     25.0%     50.0%     75.0%     97.5% 
      Symbol   Float64   Float64   Float64   Float64   Float64 

           ν    0.3741    0.6856    0.9406    1.3410    2.4627
           σ    2.0262    2.3547    2.5815    2.8333    3.4249
        β[1]   19.2904   27.0648   30.1711   33.0837   38.8812
        β[2]   -0.0587   -0.0458   -0.0393   -0.0328   -0.0202
        β[3]   -4.3684   -3.3394   -2.8206   -2.2711   -1.0594
        β[4]   -0.2602    0.7464    1.3014    1.8909    3.1216
        
julia> plot(container.chain)
```
