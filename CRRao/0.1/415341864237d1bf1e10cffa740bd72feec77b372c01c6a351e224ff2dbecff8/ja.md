```julia
fit(formula::FormulaTerm, data::DataFrame, modelClass::LogisticRegression, Link::CRRaoLink, prior::Prior_TDist, h::Float64 = 1.0, level::Float64 = 0.95, sim_size::Int64 = 1000)
```

入力データに対して、提供された `Link` 関数を用いた T-Dist プライヤーでベイジアンロジスティック回帰モデルをフィットします。

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
julia> CRRao.set_rng(StableRNG(7740));
StableRNGs.LehmerRNG(state=0x00000000000000000000000000003c79)
julia> container_logit = fit(@formula(Vote ~ Age + Race + Income + Educate), turnout, LogisticRegression(), Logit(), Prior_TDist())
┌ Info: Found initial step size
└   ϵ = 0.003125
┌ Warning: The current proposal will be rejected due to numerical error(s).
│   isfinite.((θ, r, ℓπ, ℓκ)) = (true, false, false, false)
└ @ AdvancedHMC ~/.julia/packages/AdvancedHMC/iWHPQ/src/hamiltonian.jl:47
Chains MCMC chain (1000×19×1 Array{Float64, 3}):

Iterations        = 501:1:1500
Number of chains  = 1
Samples per chain = 1000
Wall duration     = 39.94 seconds
Compute duration  = 39.94 seconds
parameters        = λ, ν, β[1], β[2], β[3], β[4], β[5]
internals         = lp, n_steps, is_accept, acceptance_rate, log_density, hamiltonian_energy, hamiltonian_energy_error, max_hamiltonian_energy_error, tree_depth, numerical_error, step_size, nom_step_size

Summary Statistics
  parameters      mean       std   naive_se      mcse        ess      rhat   ess_per_sec 
      Symbol   Float64   Float64    Float64   Float64    Float64   Float64       Float64 

           λ    0.7011    0.3630     0.0115    0.0144   545.8105    0.9991       13.6671
           ν    1.4459    0.9166     0.0290    0.0334   691.7171    1.0066       17.3206
        β[1]   -2.9624    0.3175     0.0100    0.0120   727.4172    0.9999       18.2146
        β[2]    0.0279    0.0034     0.0001    0.0001   939.5146    0.9993       23.5255
        β[3]    0.2331    0.1479     0.0047    0.0046   742.9274    0.9992       18.6029
        β[4]    0.1750    0.0259     0.0008    0.0009   695.4691    0.9994       17.4146
        β[5]    0.1729    0.0197     0.0006    0.0008   697.3021    0.9994       17.4605

Quantiles
  parameters      2.5%     25.0%     50.0%     75.0%     97.5% 
      Symbol   Float64   Float64   Float64   Float64   Float64 

           λ    0.2980    0.4622    0.6229    0.8441    1.6138
           ν    0.4603    0.8479    1.2170    1.7611    3.9754
        β[1]   -3.5783   -3.1642   -2.9738   -2.7651   -2.3367
        β[2]    0.0210    0.0257    0.0279    0.0302    0.0347
        β[3]   -0.0383    0.1349    0.2251    0.3318    0.5290
        β[4]    0.1262    0.1577    0.1741    0.1920    0.2272
        β[5]    0.1349    0.1604    0.1723    0.1861    0.2119

julia> CRRao.set_rng(StableRNG(7740))
julia> container_probit = fit(@formula(Vote ~ Age + Race + Income + Educate), turnout, LogisticRegression(), Probit(), Prior_TDist())
┌ Info: Found initial step size
└   ϵ = 0.00078125
Chains MCMC chain (1000×19×1 Array{Float64, 3}):

Iterations        = 501:1:1500
Number of chains  = 1
Samples per chain = 1000
Wall duration     = 47.56 seconds
Compute duration  = 47.56 seconds
parameters        = λ, ν, β[1], β[2], β[3], β[4], β[5]
internals         = lp, n_steps, is_accept, acceptance_rate, log_density, hamiltonian_energy, hamiltonian_energy_error, max_hamiltonian_energy_error, tree_depth, numerical_error, step_size, nom_step_size

Summary Statistics
  parameters      mean       std   naive_se      mcse        ess      rhat   ess_per_sec 
      Symbol   Float64   Float64    Float64   Float64    Float64   Float64       Float64 

           λ    0.6284    0.2643     0.0084    0.0085   759.3697    0.9997       15.9656
           ν    1.7113    1.3044     0.0412    0.0491   715.9368    0.9996       15.0524
        β[1]   -1.7098    0.1909     0.0060    0.0064   609.6431    0.9994       12.8176
        β[2]    0.0162    0.0020     0.0001    0.0001   943.5295    0.9992       19.8375
        β[3]    0.1525    0.0878     0.0028    0.0026   945.7419    0.9990       19.8840
        β[4]    0.0966    0.0145     0.0005    0.0005   942.0548    0.9990       19.8065
        β[5]    0.1017    0.0116     0.0004    0.0004   580.8348    0.9993       12.2119

Quantiles
  parameters      2.5%     25.0%     50.0%     75.0%     97.5% 
      Symbol   Float64   Float64   Float64   Float64   Float64 

           λ    0.2854    0.4398    0.5684    0.7640    1.2603
           ν    0.4877    0.9461    1.3453    2.0327    5.1304
        β[1]   -2.0824   -1.8335   -1.7198   -1.5816   -1.3325
        β[2]    0.0120    0.0148    0.0162    0.0176    0.0198
        β[3]   -0.0282    0.0960    0.1541    0.2147    0.3217
        β[4]    0.0687    0.0869    0.0970    0.1063    0.1240
        β[5]    0.0787    0.0937    0.1015    0.1095    0.1241

julia> CRRao.set_rng(StableRNG(7740))
julia> container_cloglog = fit(@formula(Vote ~ Age + Race + Income + Educate), turnout, LogisticRegression(), Cloglog(), Prior_TDist())
┌ Info: Found initial step size
└   ϵ = 0.0015625
Chains MCMC chain (10000×19×1 Array{Float64, 3}):

Iterations        = 1001:1:11000
Number of chains  = 1
Samples per chain = 10000
Wall duration     = 666.27 seconds
Compute duration  = 666.27 seconds
parameters        = λ, ν, β[1], β[2], β[3], β[4], β[5]
internals         = lp, n_steps, is_accept, acceptance_rate, log_density, hamiltonian_energy, hamiltonian_energy_error, max_hamiltonian_energy_error, tree_depth, numerical_error, step_size, nom_step_size

Summary Statistics
  parameters      mean       std   naive_se      mcse          ess      rhat   ess_per_sec 
      Symbol   Float64   Float64    Float64   Float64      Float64   Float64       Float64 

           λ    0.6312    0.2782     0.0028    0.0040    4453.1117    0.9999        6.6837
           ν    1.6104    1.3172     0.0132    0.0241    2233.9301    1.0000        3.3529
        β[1]   -1.9118    0.1841     0.0018    0.0019    8957.3062    0.9999       13.4440
        β[2]    0.0146    0.0018     0.0000    0.0000    9811.4797    0.9999       14.7260
        β[3]    0.1736    0.0851     0.0009    0.0013    3552.7097    0.9999        5.3323
        β[4]    0.0769    0.0119     0.0001    0.0001   11861.3612    1.0002       17.8027
        β[5]    0.0971    0.0109     0.0001    0.0001   11028.1160    1.0002       16.5521

Quantiles
  parameters      2.5%     25.0%     50.0%     75.0%     97.5% 
      Symbol   Float64   Float64   Float64   Float64   Float64 

           λ    0.2858    0.4424    0.5693    0.7569    1.3451
           ν    0.5054    0.8957    1.2752    1.8894    4.6403
        β[1]   -2.2751   -2.0344   -1.9134   -1.7884   -1.5464
        β[2]    0.0110    0.0134    0.0146    0.0158    0.0182
        β[3]    0.0072    0.1164    0.1742    0.2325    0.3366
        β[4]    0.0534    0.0689    0.0768    0.0849    0.1003
        β[5]    0.0760    0.0897    0.0970    0.1044    0.1187

julia> CRRao.set_rng(StableRNG(7740))
julia> container_cauchit = fit(@formula(Vote ~ Age + Race + Income + Educate), turnout, LogisticRegression(), Cauchit(), Prior_TDist())
┌ Info: Found initial step size
└   ϵ = 0.8
Chains MCMC chain (1000×19×1 Array{Float64, 3}):

Iterations        = 501:1:1500
Number of chains  = 1
Samples per chain = 1000
Wall duration     = 68.68 seconds
Compute duration  = 68.68 seconds
parameters        = λ, ν, β[1], β[2], β[3], β[4], β[5]
internals         = lp, n_steps, is_accept, acceptance_rate, log_density, hamiltonian_energy, hamiltonian_energy_error, max_hamiltonian_energy_error, tree_depth, numerical_error, step_size, nom_step_size

Summary Statistics
  parameters      mean       std   naive_se      mcse        ess      rhat   ess_per_sec 
      Symbol   Float64   Float64    Float64   Float64    Float64   Float64       Float64 

           λ    0.6907    0.3474     0.0110    0.0126   712.4682    0.9990       10.3736
           ν    1.5930    1.7268     0.0546    0.1194   179.2215    0.9991        2.6095
        β[1]   -3.1058    0.3806     0.0120    0.0152   645.0360    0.9992        9.3918
        β[2]    0.0301    0.0043     0.0001    0.0002   824.3969    0.9991       12.0033
        β[3]    0.1578    0.1461     0.0046    0.0045   903.3324    1.0037       13.1526
        β[4]    0.2375    0.0421     0.0013    0.0019   471.7863    1.0106        6.8692
        β[5]    0.1668    0.0235     0.0007    0.0010   645.8576    0.9990        9.4037

Quantiles
  parameters      2.5%     25.0%     50.0%     75.0%     97.5% 
      Symbol   Float64   Float64   Float64   Float64   Float64 

           λ    0.2894    0.4587    0.6085    0.8172    1.5353
           ν    0.4751    0.8676    1.2220    1.7524    5.1716
        β[1]   -3.8599   -3.3612   -3.1010   -2.8637   -2.3669
        β[2]    0.0218    0.0271    0.0300    0.0330    0.0388
        β[3]   -0.1336    0.0643    0.1646    0.2552    0.4311
        β[4]    0.1592    0.2092    0.2368    0.2650    0.3271
        β[5]    0.1218    0.1508    0.1661    0.1819    0.2157
```
