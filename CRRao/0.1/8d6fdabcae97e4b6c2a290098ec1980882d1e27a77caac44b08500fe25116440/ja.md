```julia
fit(formula::FormulaTerm, data::DataFrame, modelClass::LinearRegression, prior::Prior_Cauchy, sim_size::Int64 = 1000)
```

Cauchy事前分布を用いて入力データにベイズ線形回帰モデルを適合させます。

# 例

```julia-repl
julia> using CRRao, RDatasets, StableRNGs, StatsModels
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
  
julia> container = fit(@formula(MPG ~ HP + WT + Gear), df, LinearRegression(), Prior_Cauchy(), 1000)
┌ Info: Found initial step size
└   ϵ = 0.000390625
Chains MCMC chain (1000×17×1 Array{Float64, 3}):

Iterations        = 501:1:1500
Number of chains  = 1
Samples per chain = 1000
Wall duration     = 0.75 seconds
Compute duration  = 0.75 seconds
parameters        = σ, β[1], β[2], β[3], β[4]
internals         = lp, n_steps, is_accept, acceptance_rate, log_density, hamiltonian_energy, hamiltonian_energy_error, max_hamiltonian_energy_error, tree_depth, numerical_error, step_size, nom_step_size

Summary Statistics
  parameters      mean       std   naive_se      mcse        ess      rhat   ess_per_sec 
      Symbol   Float64   Float64    Float64   Float64    Float64   Float64       Float64 

           σ    2.5922    0.3538     0.0112    0.0173   425.5703    0.9993      570.4696
        β[1]   30.0880    4.7389     0.1499    0.2468   229.5288    1.0065      307.6794
        β[2]   -0.0395    0.0100     0.0003    0.0005   329.9440    1.0007      442.2842
        β[3]   -2.8197    0.8453     0.0267    0.0475   218.5494    1.0049      292.9617
        β[4]    1.3148    0.8630     0.0273    0.0428   245.2960    1.0057      328.8150

Quantiles
  parameters      2.5%     25.0%     50.0%     75.0%     97.5% 
      Symbol   Float64   Float64   Float64   Float64   Float64 

           σ    2.0287    2.3224    2.5539    2.8095    3.3997
        β[1]   20.5220   26.8878   30.1467   33.4241   38.9193
        β[2]   -0.0600   -0.0454   -0.0400   -0.0334   -0.0192
        β[3]   -4.4784   -3.3625   -2.8345   -2.2815   -1.1017
        β[4]   -0.2688    0.6897    1.3047    1.8932    3.0914
```
