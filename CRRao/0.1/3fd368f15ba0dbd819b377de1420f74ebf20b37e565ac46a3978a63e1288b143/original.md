```julia
fit(formula::FormulaTerm, data::DataFrame, modelClass::LogisticRegression, Link::CRRaoLink, prior::Prior_Ridge, h::Float64 = 0.1, level::Float64 = 0.95, sim_size::Int64 = 1000)
```

Fit a Bayesian Logistic Regression model on the input data with a Ridge prior with the provided `Link` function.

# Example

```julia-repl
julia> using CRRao, RDatasets, StableRNGs, StatsModels
julia> turnout = dataset("Zelig", "turnout")
2000×5 DataFrame
  Row │ Race   Age    Educate  Income   Vote  
      │ Cat…   Int32  Float64  Float64  Int32 
──────┼───────────────────────────────────────
    1 │ white     60     14.0   3.3458      1
    2 │ white     51     10.0   1.8561      0
    3 │ white     24     12.0   0.6304      0
    4 │ white     38      8.0   3.4183      1
  ⋮   │   ⋮      ⋮       ⋮        ⋮       ⋮
 1998 │ white     51     16.0   7.8949      1
 1999 │ white     22     10.0   2.4811      0
 2000 │ white     59     10.0   0.5523      0

julia> CRRao.set_rng(StableRNG(123))
StableRNGs.LehmerRNG(state=0x000000000000000000000000000000f7)

julia> container_logit = fit(@formula(Vote ~ Age + Race + Income + Educate), turnout, LogisticRegression(), Logit(), Prior_Ridge())
Chains MCMC chain (1000×18×1 Array{Float64, 3}):

Iterations        = 501:1:1500
Number of chains  = 1
Samples per chain = 1000
Wall duration     = 46.7 seconds
Compute duration  = 46.7 seconds
parameters        = λ, β[1], β[2], β[3], β[4], β[5]
internals         = lp, n_steps, is_accept, acceptance_rate, log_density, hamiltonian_energy, hamiltonian_energy_error, max_hamiltonian_energy_error, tree_depth, numerical_error, step_size, nom_step_size

Summary Statistics
  parameters      mean       std   naive_se      mcse        ess      rhat   ess_per_sec 
      Symbol   Float64   Float64    Float64   Float64    Float64   Float64       Float64 

           λ    1.4907    0.5918     0.0187    0.0236   593.6860    0.9990       12.7136
        β[1]   -2.8684    0.3406     0.0108    0.0151   502.0358    1.0001       10.7509
        β[2]    0.0271    0.0036     0.0001    0.0001   617.1201    1.0001       13.2154
        β[3]    0.2266    0.1434     0.0045    0.0047   830.1625    0.9996       17.7776
        β[4]    0.1793    0.0273     0.0009    0.0010   830.0115    1.0018       17.7744
        β[5]    0.1677    0.0203     0.0006    0.0009   530.2735    1.0002       11.3556

Quantiles
  parameters      2.5%     25.0%     50.0%     75.0%     97.5% 
      Symbol   Float64   Float64   Float64   Float64   Float64 

           λ    0.7846    1.0730    1.3581    1.7063    3.0609
        β[1]   -3.5602   -3.1138   -2.8687   -2.6160   -2.2454
        β[2]    0.0202    0.0247    0.0270    0.0294    0.0347
        β[3]   -0.0541    0.1323    0.2315    0.3264    0.4980
        β[4]    0.1281    0.1597    0.1783    0.1989    0.2336
        β[5]    0.1276    0.1548    0.1675    0.1804    0.2104

julia> predict(container_logit,turnout)
julia> CRRao.set_rng(StableRNG(123))

julia> container_probit = fit(@formula(Vote ~ Age + Race + Income + Educate), turnout, LogisticRegression(), Probit(), Prior_Ridge())
Chains MCMC chain (1000×18×1 Array{Float64, 3}):

Iterations        = 501:1:1500
Number of chains  = 1
Samples per chain = 1000
Wall duration     = 35.35 seconds
Compute duration  = 35.35 seconds
parameters        = λ, β[1], β[2], β[3], β[4], β[5]
internals         = lp, n_steps, is_accept, acceptance_rate, log_density, hamiltonian_energy, hamiltonian_energy_error, max_hamiltonian_energy_error, tree_depth, numerical_error, step_size, nom_step_size

Summary Statistics
  parameters      mean       std   naive_se      mcse        ess      rhat   ess_per_sec 
      Symbol   Float64   Float64    Float64   Float64    Float64   Float64       Float64 

           λ    0.9120    0.3882     0.0123    0.0137   592.9548    1.0005       16.7719
        β[1]   -1.6775    0.1843     0.0058    0.0094   452.5107    0.9996       12.7994
        β[2]    0.0159    0.0020     0.0001    0.0001   699.2797    0.9996       19.7794
        β[3]    0.1473    0.0868     0.0027    0.0032   609.4328    0.9990       17.2380
        β[4]    0.0966    0.0153     0.0005    0.0006   556.8599    0.9991       15.7510
        β[5]    0.1004    0.0119     0.0004    0.0006   408.9705    0.9993       11.5679

Quantiles
  parameters      2.5%     25.0%     50.0%     75.0%     97.5% 
      Symbol   Float64   Float64   Float64   Float64   Float64 

           λ    0.4408    0.6582    0.8190    1.0636    1.8731
        β[1]   -2.0316   -1.8051   -1.6756   -1.5634   -1.2959
        β[2]    0.0121    0.0145    0.0159    0.0172    0.0201
        β[3]   -0.0286    0.0907    0.1496    0.2102    0.3104
        β[4]    0.0665    0.0863    0.0969    0.1070    0.1269
        β[5]    0.0771    0.0919    0.1004    0.1084    0.1238

julia> predict(container_probit,turnout)

julia> CRRao.set_rng(StableRNG(123))
julia> container_cloglog = fit(@formula(Vote ~ Age + Race + Income + Educate), turnout, LogisticRegression(), Cloglog(), Prior_Ridge())
Chains MCMC chain (1000×18×1 Array{Float64, 3}):

Iterations        = 501:1:1500
Number of chains  = 1
Samples per chain = 1000
Wall duration     = 44.56 seconds
Compute duration  = 44.56 seconds
parameters        = λ, β[1], β[2], β[3], β[4], β[5]
internals         = lp, n_steps, is_accept, acceptance_rate, log_density, hamiltonian_energy, hamiltonian_energy_error, max_hamiltonian_energy_error, tree_depth, numerical_error, step_size, nom_step_size

Summary Statistics
  parameters      mean       std   naive_se      mcse        ess      rhat   ess_per_sec 
      Symbol   Float64   Float64    Float64   Float64    Float64   Float64       Float64 

           λ    1.0207    0.4636     0.0147    0.0250   250.5938    1.0007        5.6241
        β[1]   -1.8739    0.1944     0.0061    0.0082   486.4861    0.9992       10.9183
        β[2]    0.0143    0.0018     0.0001    0.0001   693.4025    0.9990       15.5621
        β[3]    0.1715    0.0822     0.0026    0.0029   668.5177    0.9993       15.0037
        β[4]    0.0775    0.0114     0.0004    0.0003   767.3234    0.9991       17.2212
        β[5]    0.0950    0.0110     0.0003    0.0004   523.2168    0.9999       11.7426

Quantiles
  parameters      2.5%     25.0%     50.0%     75.0%     97.5% 
      Symbol   Float64   Float64   Float64   Float64   Float64 

           λ    0.5094    0.7421    0.9210    1.1688    2.1113
        β[1]   -2.2663   -1.9963   -1.8787   -1.7465   -1.5043
        β[2]    0.0106    0.0131    0.0143    0.0155    0.0180
        β[3]    0.0140    0.1159    0.1730    0.2232    0.3280
        β[4]    0.0562    0.0700    0.0777    0.0849    0.1009
        β[5]    0.0728    0.0879    0.0948    0.1019    0.1164
        
julia> CRRao.set_rng(StableRNG(123))
julia> container_cauchit = fit(@formula(Vote ~ Age + Race + Income + Educate), turnout, LogisticRegression(), Cauchit(), Prior_Ridge())
┌ Info: Found initial step size
└   ϵ = 0.025
Chains MCMC chain (1000×18×1 Array{Float64, 3}):

Iterations        = 501:1:1500
Number of chains  = 1
Samples per chain = 1000
Wall duration     = 32.18 seconds
Compute duration  = 32.18 seconds
parameters        = λ, β[1], β[2], β[3], β[4], β[5]
internals         = lp, n_steps, is_accept, acceptance_rate, log_density, hamiltonian_energy, hamiltonian_energy_error, max_hamiltonian_energy_error, tree_depth, numerical_error, step_size, nom_step_size

Summary Statistics
  parameters      mean       std   naive_se      mcse        ess      rhat   ess_per_sec 
      Symbol   Float64   Float64    Float64   Float64    Float64   Float64       Float64 

           λ    1.6145    0.8633     0.0273    0.0605   263.9458    1.0083        8.2032
        β[1]   -2.9672    0.4041     0.0128    0.0194   425.5258    0.9996       13.2249
        β[2]    0.0287    0.0043     0.0001    0.0002   514.5857    1.0017       15.9928
        β[3]    0.1590    0.1530     0.0048    0.0072   635.2277    0.9990       19.7423
        β[4]    0.2406    0.0399     0.0013    0.0014   654.7789    0.9992       20.3499
        β[5]    0.1590    0.0248     0.0008    0.0011   470.3448    0.9992       14.6179

Quantiles
  parameters      2.5%     25.0%     50.0%     75.0%     97.5% 
      Symbol   Float64   Float64   Float64   Float64   Float64 

           λ    0.7688    1.1244    1.3980    1.8607    3.5488
        β[1]   -3.7871   -3.2405   -2.9510   -2.6879   -2.2261
        β[2]    0.0201    0.0256    0.0285    0.0315    0.0374
        β[3]   -0.1352    0.0549    0.1552    0.2700    0.4495
        β[4]    0.1679    0.2128    0.2384    0.2667    0.3222
        β[5]    0.1142    0.1420    0.1580    0.1754    0.2121

```
