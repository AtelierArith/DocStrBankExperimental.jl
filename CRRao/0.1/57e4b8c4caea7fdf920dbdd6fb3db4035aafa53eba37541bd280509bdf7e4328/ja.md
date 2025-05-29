```julia
fit(formula::FormulaTerm, data::DataFrame, modelClass::LinearRegression, prior::Prior_Ridge, h::Float64 = 0.01, sim_size::Int64 = 1000)
```

入力データに対してリッジ事前分布を用いたベイズ線形回帰モデルをフィットします。

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
  
julia> container = fit(@formula(MPG ~ HP + WT + Gear), df, LinearRegression(), Prior_Ridge())
┌ Info: Found initial step size
└   ϵ = 0.00078125
Chains MCMC chain (1000×18×1 Array{Float64, 3}):

Iterations        = 501:1:1500
Number of chains  = 1
Samples per chain = 1000
Wall duration     = 3.8 seconds
Compute duration  = 3.8 seconds
parameters        = v, σ, β[1], β[2], β[3], β[4]
internals         = lp, n_steps, is_accept, acceptance_rate, log_density, hamiltonian_energy, hamiltonian_energy_error, max_hamiltonian_energy_error, tree_depth, numerical_error, step_size, nom_step_size

Summary Statistics
  parameters      mean       std   naive_se      mcse        ess      rhat   ess_per_sec 
      Symbol   Float64   Float64    Float64   Float64    Float64   Float64       Float64 

           v    6.7326    4.0697     0.1287    0.2091   385.1846    1.0072      101.3377
           σ    2.6887    0.3769     0.0119    0.0173   454.6314    0.9992      119.6084
        β[1]   28.5712    5.4865     0.1735    0.2940   275.1500    0.9999       72.3888
        β[2]   -0.0395    0.0101     0.0003    0.0005   449.6762    0.9994      118.3047
        β[3]   -2.7071    0.9612     0.0304    0.0495   304.8328    1.0005       80.1981
        β[4]    1.6235    0.9894     0.0313    0.0525   293.2379    0.9998       77.1476

Quantiles
  parameters      2.5%     25.0%     50.0%     75.0%     97.5% 
      Symbol   Float64   Float64   Float64   Float64   Float64 

           v    2.4199    4.3092    5.8397    8.0100   15.9390
           σ    2.0880    2.4184    2.6358    2.9308    3.5183
        β[1]   17.0694   25.0878   28.6635   32.2368   39.1438
        β[2]   -0.0594   -0.0462   -0.0398   -0.0327   -0.0198
        β[3]   -4.5435   -3.3350   -2.6938   -2.1350   -0.7247
        β[4]   -0.2647    0.9636    1.5983    2.2412    3.6841
```
