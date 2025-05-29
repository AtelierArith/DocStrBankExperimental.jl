```julia
fit(formula::FormulaTerm, data::DataFrame, modelClass::LogisticRegression, Link::CRRaoLink, prior::Prior_Cauchy, h::Float64 = 0.1, level::Float64 = 0.95, sim_size::Int64 = 1000)
```

入力データに対して、指定された `Link` 関数を用いたコーシー事前分布のベイズロジスティック回帰モデルをフィットします。

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
                             1993 rows omitted
julia> container_logit = fit(@formula(Vote ~ Age + Race + Income + Educate), turnout, LogisticRegression(), Logit(), Prior_Cauchy())
┌ Info: Found initial step size
└   ϵ = 0.0015625
Chains MCMC chain (1000×18×1 Array{Float64, 3}):

Iterations        = 501:1:1500
Number of chains  = 1
Samples per chain = 1000
Wall duration     = 32.88 seconds
Compute duration  = 32.88 seconds
parameters        = λ, β[1], β[2], β[3], β[4], β[5]
internals         = lp, n_steps, is_accept, acceptance_rate, log_density, hamiltonian_energy, hamiltonian_energy_error, max_hamiltonian_energy_error, tree_depth, numerical_error, step_size, nom_step_size

Summary Statistics
  parameters      mean       std   naive_se      mcse        ess      rhat   ess_per_sec 
      Symbol   Float64   Float64    Float64   Float64    Float64   Float64       Float64 

           λ    0.3048    0.2245     0.0071    0.0092   732.5949    0.9994       22.2829
        β[1]   -2.9536    0.3307     0.0105    0.0151   501.8962    1.0078       15.2659
        β[2]    0.0282    0.0035     0.0001    0.0001   814.6017    1.0013       24.7773
        β[3]    0.1818    0.1379     0.0044    0.0049   641.2468    1.0105       19.5044
        β[4]    0.1781    0.0279     0.0009    0.0009   873.2256    0.9992       26.5604
        β[5]    0.1738    0.0201     0.0006    0.0008   612.2187    1.0022       18.6215

Quantiles
  parameters      2.5%     25.0%     50.0%     75.0%     97.5% 
      Symbol   Float64   Float64   Float64   Float64   Float64 

           λ    0.0701    0.1564    0.2435    0.3783    0.9120
        β[1]   -3.5915   -3.1683   -2.9647   -2.7330   -2.2954
        β[2]    0.0214    0.0258    0.0282    0.0307    0.0350
        β[3]   -0.0673    0.0823    0.1762    0.2728    0.4755
        β[4]    0.1237    0.1595    0.1787    0.1962    0.2341
        β[5]    0.1358    0.1608    0.1735    0.1866    0.2164

julia> container_probit = fit(@formula(Vote ~ Age + Race + Income + Educate), turnout, LogisticRegression(), Probit(), Prior_Cauchy())
Chains MCMC chain (1000×18×1 Array{Float64, 3}):

Iterations        = 501:1:1500
Number of chains  = 1
Samples per chain = 1000
Wall duration     = 92.1 seconds
Compute duration  = 92.1 seconds
parameters        = λ, β[1], β[2], β[3], β[4], β[5]
internals         = lp, n_steps, is_accept, acceptance_rate, log_density, hamiltonian_energy, hamiltonian_energy_error, max_hamiltonian_energy_error, tree_depth, numerical_error, step_size, nom_step_size

Summary Statistics
  parameters      mean       std   naive_se      mcse         ess      rhat   ess_per_sec 
      Symbol   Float64   Float64    Float64   Float64     Float64   Float64       Float64 

           λ    0.1889    0.1676     0.0053    0.0102    213.5688    1.0055        2.3189
        β[1]   -1.6968    0.1900     0.0060    0.0059    668.5132    0.9997        7.2586
        β[2]    0.0164    0.0020     0.0001    0.0001    844.5946    0.9994        9.1704
        β[3]    0.1155    0.0820     0.0026    0.0050    351.2848    1.0087        3.8142
        β[4]    0.0955    0.0151     0.0005    0.0004   1072.1826    0.9992       11.6415
        β[5]    0.1029    0.0117     0.0004    0.0004    781.5659    0.9991        8.4861

Quantiles
  parameters      2.5%     25.0%     50.0%     75.0%     97.5% 
      Symbol   Float64   Float64   Float64   Float64   Float64 

           λ    0.0368    0.0847    0.1335    0.2284    0.6325
        β[1]   -2.0732   -1.8312   -1.6971   -1.5656   -1.3258
        β[2]    0.0124    0.0150    0.0163    0.0177    0.0203
        β[3]   -0.0366    0.0566    0.1128    0.1706    0.2800
        β[4]    0.0657    0.0852    0.0958    0.1058    0.1245
        β[5]    0.0798    0.0949    0.1028    0.1111    0.1251
julia> container_cloglog = fit(@formula(Vote ~ Age + Race + Income + Educate), turnout, LogisticRegression(), Cloglog(), Prior_Cauchy())
Chains MCMC chain (1000×18×1 Array{Float64, 3}):

Iterations        = 501:1:1500
Number of chains  = 1
Samples per chain = 1000
Wall duration     = 41.19 seconds
Compute duration  = 41.19 seconds
parameters        = λ, β[1], β[2], β[3], β[4], β[5]
internals         = lp, n_steps, is_accept, acceptance_rate, log_density, hamiltonian_energy, hamiltonian_energy_error, max_hamiltonian_energy_error, tree_depth, numerical_error, step_size, nom_step_size

Summary Statistics
  parameters      mean       std   naive_se      mcse        ess      rhat   ess_per_sec 
      Symbol   Float64   Float64    Float64   Float64    Float64   Float64       Float64 

           λ    0.1839    0.2072     0.0066    0.0085   681.7783    0.9991       16.5520
        β[1]   -1.8712    0.1883     0.0060    0.0068   568.8922    0.9993       13.8114
        β[2]    0.0146    0.0019     0.0001    0.0001   866.0645    0.9990       21.0261
        β[3]    0.1383    0.0857     0.0027    0.0037   500.3015    1.0037       12.1462
        β[4]    0.0765    0.0117     0.0004    0.0004   955.1365    0.9991       23.1886
        β[5]    0.0965    0.0114     0.0004    0.0004   612.5153    1.0007       14.8705

Quantiles
  parameters      2.5%     25.0%     50.0%     75.0%     97.5% 
      Symbol   Float64   Float64   Float64   Float64   Float64 

           λ    0.0346    0.0889    0.1368    0.2232    0.5814
        β[1]   -2.2534   -2.0036   -1.8581   -1.7428   -1.5302
        β[2]    0.0112    0.0133    0.0145    0.0159    0.0184
        β[3]   -0.0102    0.0751    0.1357    0.1937    0.3198
        β[4]    0.0538    0.0689    0.0768    0.0842    0.1003
        β[5]    0.0750    0.0883    0.0960    0.1042    0.1206

julia> container_cauchit = fit(@formula(Vote ~ Age + Race + Income + Educate), turnout, LogisticRegression(), Cauchit(), Prior_Cauchy())
Chains MCMC chain (1000×18×1 Array{Float64, 3}):

Iterations        = 501:1:1500
Number of chains  = 1
Samples per chain = 1000
Wall duration     = 26.07 seconds
Compute duration  = 26.07 seconds
parameters        = λ, β[1], β[2], β[3], β[4], β[5]
internals         = lp, n_steps, is_accept, acceptance_rate, log_density, hamiltonian_energy, hamiltonian_energy_error, max_hamiltonian_energy_error, tree_depth, numerical_error, step_size, nom_step_size

Summary Statistics
  parameters      mean       std   naive_se      mcse        ess      rhat   ess_per_sec 
      Symbol   Float64   Float64    Float64   Float64    Float64   Float64       Float64 

           λ    0.3142    0.2296     0.0073    0.0065   775.1497    1.0000       29.7334
        β[1]   -3.0635    0.3940     0.0125    0.0142   616.9777    1.0020       23.6662
        β[2]    0.0299    0.0045     0.0001    0.0001   758.2408    1.0016       29.0848
        β[3]    0.1211    0.1321     0.0042    0.0050   551.1313    0.9992       21.1404
        β[4]    0.2345    0.0408     0.0013    0.0014   670.1954    1.0003       25.7075
        β[5]    0.1671    0.0249     0.0008    0.0009   631.3726    1.0014       24.2184

Quantiles
  parameters      2.5%     25.0%     50.0%     75.0%     97.5% 
      Symbol   Float64   Float64   Float64   Float64   Float64 

           λ    0.0654    0.1638    0.2555    0.3933    0.9454
        β[1]   -3.8138   -3.3366   -3.0547   -2.7857   -2.3285
        β[2]    0.0211    0.0270    0.0301    0.0329    0.0384
        β[3]   -0.1105    0.0282    0.1117    0.2168    0.3907
        β[4]    0.1603    0.2064    0.2324    0.2627    0.3157
        β[5]    0.1166    0.1501    0.1669    0.1839    0.2152
```
