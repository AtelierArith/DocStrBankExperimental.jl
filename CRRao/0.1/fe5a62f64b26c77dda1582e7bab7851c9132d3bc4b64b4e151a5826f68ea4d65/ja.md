```julia
fit(formula::FormulaTerm, data::DataFrame, modelClass::LogisticRegression, Link::CRRaoLink, prior::Prior_Laplace, h::Float64 = 0.1, level::Float64 = 0.95, sim_size::Int64 = 1000)
```

入力データに対して、指定された `Link` 関数を用いたラプラス事前分布のベイズロジスティック回帰モデルをフィットします。

# 例

```julia-repl
julia> using CRRao, RDatasets, StableRNGs, StatsModels
julia> CRRao.set_rng(StableRNG(123))
StableRNGs.LehmerRNG(state=0x000000000000000000000000000000f7)
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

julia> container_logit = fit(@formula(Vote ~ Age + Race + Income + Educate), turnout, LogisticRegression(), Logit(), Prior_Laplace())
┌ Info: Found initial step size
└   ϵ = 0.0015625
Chains MCMC chain (1000×18×1 Array{Float64, 3}):

Iterations        = 501:1:1500
Number of chains  = 1
Samples per chain = 1000
Wall duration     = 47.58 seconds
Compute duration  = 47.58 seconds
parameters        = λ, β[1], β[2], β[3], β[4], β[5]
internals         = lp, n_steps, is_accept, acceptance_rate, log_density, hamiltonian_energy, hamiltonian_energy_error, max_hamiltonian_energy_error, tree_depth, numerical_error, step_size, nom_step_size

Summary Statistics
  parameters      mean       std   naive_se      mcse        ess      rhat   ess_per_sec 
      Symbol   Float64   Float64    Float64   Float64    Float64   Float64       Float64 

          λ    0.8459    0.4712     0.0149    0.0148   821.7483    0.9990       17.2709
        β[1]   -2.8796    0.3230     0.0102    0.0168   358.1394    1.0043        7.5271
        β[2]    0.0273    0.0032     0.0001    0.0001   629.0124    0.9999       13.2201
        β[3]    0.2138    0.1418     0.0045    0.0049   697.8744    0.9995       14.6674
        β[4]    0.1774    0.0264     0.0008    0.0009   779.0814    0.9998       16.3741
        β[5]    0.1692    0.0201     0.0006    0.0010   363.7691    1.0071        7.6454

Quantiles
  parameters      2.5%     25.0%     50.0%     75.0%     97.5% 
      Symbol   Float64   Float64   Float64   Float64   Float64 

          λ    0.3275    0.5375    0.7244    1.0189    2.1072
        β[1]   -3.5527   -3.0956   -2.8824   -2.6539   -2.2616
        β[2]    0.0212    0.0250    0.0273    0.0294    0.0336
        β[3]   -0.0401    0.1143    0.2130    0.3094    0.4914
        β[4]    0.1283    0.1597    0.1768    0.1953    0.2282
        β[5]    0.1282    0.1562    0.1693    0.1828    0.2087
                             

julia> container_probit = fit(@formula(Vote ~ Age + Race + Income + Educate), turnout, LogisticRegression(), Probit(), Prior_Laplace())
Chains MCMC chain (1000×18×1 Array{Float64, 3}):

Iterations        = 501:1:1500
Number of chains  = 1
Samples per chain = 1000
Wall duration     = 44.42 seconds
Compute duration  = 44.42 seconds
parameters        = λ, β[1], β[2], β[3], β[4], β[5]
internals         = lp, n_steps, is_accept, acceptance_rate, log_density, hamiltonian_energy, hamiltonian_energy_error, max_hamiltonian_energy_error, tree_depth, numerical_error, step_size, nom_step_size

Summary Statistics
  parameters      mean       std   naive_se      mcse        ess      rhat   ess_per_sec 
      Symbol   Float64   Float64    Float64   Float64    Float64   Float64       Float64 

           λ    0.5137    0.2746     0.0087    0.0090   654.5174    0.9991       14.7357
        β[1]   -1.6793    0.2013     0.0064    0.0086   640.0050    0.9991       14.4090
        β[2]    0.0160    0.0020     0.0001    0.0001   848.1151    0.9990       19.0944
        β[3]    0.1451    0.0878     0.0028    0.0037   804.2314    1.0003       18.1064
        β[4]    0.0963    0.0143     0.0005    0.0005   750.7575    1.0029       16.9025
        β[5]    0.1005    0.0118     0.0004    0.0004   696.8244    0.9991       15.6882

Quantiles
  parameters      2.5%     25.0%     50.0%     75.0%     97.5% 
      Symbol   Float64   Float64   Float64   Float64   Float64 

           λ    0.1955    0.3289    0.4496    0.6183    1.1915
        β[1]   -2.0608   -1.8105   -1.6898   -1.5374   -1.2636
        β[2]    0.0123    0.0147    0.0160    0.0174    0.0199
        β[3]   -0.0209    0.0832    0.1466    0.2063    0.3211
        β[4]    0.0686    0.0869    0.0964    0.1054    0.1258
        β[5]    0.0772    0.0925    0.1004    0.1091    0.1219

julia> CRRao.set_rng(StableRNG(123))        
julia> container_cloglog = fit(@formula(Vote ~ Age + Race + Income + Educate), turnout, LogisticRegression(), Cloglog(), Prior_Laplace())
Chains MCMC chain (1000×18×1 Array{Float64, 3}):

Iterations        = 501:1:1500
Number of chains  = 1
Samples per chain = 1000
Wall duration     = 45.03 seconds
Compute duration  = 45.03 seconds
parameters        = λ, β[1], β[2], β[3], β[4], β[5]
internals         = lp, n_steps, is_accept, acceptance_rate, log_density, hamiltonian_energy, hamiltonian_energy_error, max_hamiltonian_energy_error, tree_depth, numerical_error, step_size, nom_step_size

Summary Statistics
  parameters      mean       std   naive_se      mcse        ess      rhat   ess_per_sec 
      Symbol   Float64   Float64    Float64   Float64    Float64   Float64       Float64 

           λ    0.5670    0.3381     0.0107    0.0133   643.3993    0.9995       14.2882
        β[1]   -1.8734    0.1839     0.0058    0.0072   622.0146    0.9990       13.8133
        β[2]    0.0143    0.0017     0.0001    0.0001   869.5863    0.9992       19.3113
        β[3]    0.1671    0.0802     0.0025    0.0028   580.9503    0.9997       12.9014
        β[4]    0.0772    0.0114     0.0004    0.0004   854.8669    0.9993       18.9844
        β[5]    0.0955    0.0109     0.0003    0.0004   758.8162    0.9993       16.8513

Quantiles
  parameters      2.5%     25.0%     50.0%     75.0%     97.5% 
      Symbol   Float64   Float64   Float64   Float64   Float64 

           λ    0.2079    0.3661    0.4862    0.6688    1.3563
        β[1]   -2.2418   -1.9906   -1.8718   -1.7539   -1.5159
        β[2]    0.0109    0.0131    0.0143    0.0154    0.0176
        β[3]    0.0194    0.1086    0.1660    0.2231    0.3207
        β[4]    0.0549    0.0696    0.0772    0.0849    0.0999
        β[5]    0.0738    0.0882    0.0959    0.1031    0.1151

julia> container_cauchit = fit(@formula(Vote ~ Age + Race + Income + Educate), turnout, LogisticRegression(), Cauchit(), Prior_Laplace())
┌ Info: Found initial step size
└   ϵ = 0.00078125
Chains MCMC chain (1000×18×1 Array{Float64, 3}):

Iterations        = 501:1:1500
Number of chains  = 1
Samples per chain = 1000
Wall duration     = 42.23 seconds
Compute duration  = 42.23 seconds
parameters        = λ, β[1], β[2], β[3], β[4], β[5]
internals         = lp, n_steps, is_accept, acceptance_rate, log_density, hamiltonian_energy, hamiltonian_energy_error, max_hamiltonian_energy_error, tree_depth, numerical_error, step_size, nom_step_size

Summary Statistics
  parameters      mean       std   naive_se      mcse        ess      rhat   ess_per_sec 
      Symbol   Float64   Float64    Float64   Float64    Float64   Float64       Float64 

            λ    0.8480    0.4143     0.0131    0.0144   675.5220    0.9998       15.9970
        β[1]   -3.0014    0.3675     0.0116    0.0179   512.9194    0.9995       12.1464
        β[2]    0.0291    0.0042     0.0001    0.0002   668.6412    0.9994       15.8341
        β[3]    0.1403    0.1468     0.0046    0.0059   732.6106    0.9993       17.3489
        β[4]    0.2394    0.0383     0.0012    0.0019   517.9500    1.0015       12.2656
        β[5]    0.1622    0.0233     0.0007    0.0011   552.8157    0.9999       13.0912

Quantiles
  parameters      2.5%     25.0%     50.0%     75.0%     97.5% 
      Symbol   Float64   Float64   Float64   Float64   Float64 

            λ    0.3261    0.5543    0.7534    1.0416    1.8282
        β[1]   -3.7419   -3.2460   -2.9995   -2.7679   -2.2990
        β[2]    0.0210    0.0260    0.0293    0.0319    0.0380
        β[3]   -0.1352    0.0447    0.1375    0.2297    0.4357
        β[4]    0.1680    0.2130    0.2378    0.2663    0.3196
        β[5]    0.1178    0.1461    0.1615    0.1769    0.2070     
```
