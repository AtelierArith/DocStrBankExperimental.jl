```julia
fit(formula::FormulaTerm, data::DataFrame, modelClass::LinearRegression, prior::Prior_Cauchy, h::Float64 = 1.0, sim_size::Int64 = 1000)
```

入力データに対してCauchy事前分布を用いたベイズポアソン回帰モデルをフィットします。

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
julia> container = fit(@formula(Num ~ Target + Coop + NCost), sanction, PoissonRegression(), Prior_Cauchy())
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

           λ    0.8433    0.4191     0.0133    0.0170   651.9481    1.0030      357.2318
        β[1]   -1.7880    0.2531     0.0080    0.0117   440.1548    1.0012      241.1807
        β[2]    0.1374    0.0640     0.0020    0.0027   596.1778    0.9992      326.6728
        β[3]    1.1299    0.0558     0.0018    0.0018   747.2077    1.0009      409.4289
        β[4]   -0.2965    0.2204     0.0070    0.0106   526.3280    1.0032      288.3989
        β[5]    1.7036    0.0973     0.0031    0.0043   600.4246    0.9992      328.9998
        β[6]    0.3928    0.1705     0.0054    0.0068   754.6819    1.0010      413.5243

Quantiles
  parameters      2.5%     25.0%     50.0%     75.0%     97.5% 
      Symbol   Float64   Float64   Float64   Float64   Float64 

           λ    0.3101    0.5456    0.7598    1.0488    1.8316
        β[1]   -2.3023   -1.9535   -1.7797   -1.6129   -1.3056
        β[2]    0.0282    0.0920    0.1355    0.1794    0.2670
        β[3]    1.0131    1.0925    1.1303    1.1680    1.2368
        β[4]   -0.7701   -0.4356   -0.2757   -0.1448    0.1045
        β[5]    1.5159    1.6388    1.7020    1.7689    1.9046
        β[6]    0.0738    0.2632    0.3881    0.5176    0.7230
```
