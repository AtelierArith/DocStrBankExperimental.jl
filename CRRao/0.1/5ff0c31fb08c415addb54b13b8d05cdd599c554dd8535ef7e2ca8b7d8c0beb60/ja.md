```julia
fit(formula::FormulaTerm, data::DataFrame, modelClass::LinearRegression, prior::Prior_Laplace, h::Float64 = 0.01, sim_size::Int64 = 1000)
```

入力データに対してラプラス事前分布を用いたベイズ線形回帰モデルをフィットします。

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
julia> container = fit(@formula(MPG ~ HP + WT + Gear), df, LinearRegression(), Prior_Laplace())
┌ Info: Found initial step size
└   ϵ = 0.00078125
Chains MCMC chain (1000×18×1 Array{Float64, 3}):

Iterations        = 501:1:1500
Number of chains  = 1
Samples per chain = 1000
Wall duration     = 2.81 seconds
Compute duration  = 2.81 seconds
parameters        = v, σ, β[1], β[2], β[3], β[4]
internals         = lp, n_steps, is_accept, acceptance_rate, log_density, hamiltonian_energy, hamiltonian_energy_error, max_hamiltonian_energy_error, tree_depth, numerical_error, step_size, nom_step_size

Summary Statistics
  parameters      mean       std   naive_se      mcse        ess      rhat   ess_per_sec 
      Symbol   Float64   Float64    Float64   Float64    Float64   Float64       Float64 

           v    4.0802    2.9685     0.0939    0.1488   388.0064    1.0061      138.0806
           σ    2.6879    0.3859     0.0122    0.0187   334.4383    1.0153      119.0172
        β[1]   28.6972    5.2832     0.1671    0.3359   182.9859    1.0255       65.1195
        β[2]   -0.0400    0.0107     0.0003    0.0005   391.2879    1.0077      139.2484
        β[3]   -2.6644    0.9818     0.0310    0.0543   249.1040    1.0171       88.6491
        β[4]    1.5659    0.9686     0.0306    0.0613   186.8354    1.0267       66.4895

Quantiles
  parameters      2.5%     25.0%     50.0%     75.0%     97.5% 
      Symbol   Float64   Float64   Float64   Float64   Float64 

           v    1.3030    2.3492    3.2065    4.8058   12.2525
           σ    2.0493    2.4028    2.6405    2.9231    3.5532
        β[1]   17.7583   25.3061   28.8668   32.2456   38.1808
        β[2]   -0.0615   -0.0469   -0.0398   -0.0329   -0.0187
        β[3]   -4.4721   -3.3004   -2.7042   -2.0441   -0.7107
        β[4]   -0.1806    0.8682    1.5224    2.1637    3.6193
```
