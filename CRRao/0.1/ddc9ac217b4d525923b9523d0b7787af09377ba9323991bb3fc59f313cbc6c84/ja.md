```julia
fit(formula::FormulaTerm,data::DataFrame,modelClass::LogisticRegression,Link::CRRaoLink,prior::Prior_HorseShoe,level::Float64 = 0.95,sim_size::Int64 = 1000)
```

入力データに対して、提供された `Link` 関数を用いたホースシュー事前分布のベイズロジスティック回帰モデルを適合させます。

# 例

```julia-repl
julia> using CRRao, RDatasets, StableRNGs, StatsModels
julia> turnout = dataset("Zelig", "turnout");
julia> CRRao.set_rng(StableRNG(7740))
julia> container_logit = fit(@formula(Vote ~ Age + Race + Income + Educate), turnout, LogisticRegression(), Logit(), Prior_HorseShoe())
Chains MCMC chain (1000×24×1 Array{Float64, 3}):

Iterations        = 501:1:1500
Number of chains  = 1
Samples per chain = 1000
Wall duration     = 78.98 seconds
Compute duration  = 78.98 seconds
parameters        = τ, λ[1], λ[2], λ[3], λ[4], λ[5], σ, β[1], β[2], β[3], β[4], β[5]
internals         = lp, n_steps, is_accept, acceptance_rate, log_density, hamiltonian_energy, hamiltonian_energy_error, max_hamiltonian_energy_error, tree_depth, numerical_error, step_size, nom_step_size

Summary Statistics
  parameters      mean       std   naive_se      mcse         ess      rhat   ess_per_sec 
      Symbol   Float64   Float64    Float64   Float64     Float64   Float64       Float64 

           τ    0.9411    1.0672     0.0337    0.0303    817.3843    0.9990       10.3489
        λ[1]   12.1657   20.9749     0.6633    0.6373    839.0119    0.9992       10.6227
        λ[2]    0.6175    1.2944     0.0409    0.0530    564.7242    0.9997        7.1499
        λ[3]    1.0698    1.6054     0.0508    0.0564    755.8639    1.0007        9.5700
        λ[4]    1.2037    1.5510     0.0490    0.0626    601.4558    0.9993        7.6150
        λ[5]    1.4052    3.8216     0.1208    0.2157    309.1836    1.0036        3.9146
           σ    1.0562    1.7528     0.0554    0.0775    458.5741    1.0000        5.8060
        β[1]   -2.9262    0.3572     0.0113    0.0234    199.5082    1.0052        2.5260
        β[2]    0.0280    0.0037     0.0001    0.0002    335.2483    1.0029        4.2446
        β[3]    0.1541    0.1360     0.0043    0.0072    308.0926    1.0027        3.9007
        β[4]    0.1783    0.0259     0.0008    0.0009   1061.7391    0.9994       13.4426
        β[5]    0.1747    0.0217     0.0007    0.0016    150.7165    1.0082        1.9082

Quantiles
  parameters      2.5%     25.0%     50.0%     75.0%     97.5% 
      Symbol   Float64   Float64   Float64   Float64   Float64 

           τ    0.0894    0.3362    0.6462    1.1511    3.5586
        λ[1]    1.1212    3.7091    7.0026   13.2362   59.5366
        λ[2]    0.0271    0.1222    0.2984    0.6426    3.0533
        λ[3]    0.0216    0.2845    0.6136    1.2534    5.1424
        λ[4]    0.1336    0.4165    0.7458    1.3820    5.6334
        λ[5]    0.1210    0.4467    0.8046    1.3866    5.8171
           σ    0.0902    0.3277    0.5955    1.1698    4.3552
        β[1]   -3.5907   -3.1452   -2.9250   -2.6843   -2.1970
        β[2]    0.0209    0.0256    0.0279    0.0305    0.0352
        β[3]   -0.0579    0.0413    0.1396    0.2505    0.4221
        β[4]    0.1287    0.1613    0.1793    0.1962    0.2313
        β[5]    0.1345    0.1600    0.1736    0.1888    0.2162

julia> CRRao.set_rng(StableRNG(7750))
julia> container_probit = fit(@formula(Vote ~ Age + Race + Income + Educate), turnout, LogisticRegression(), Probit(), Prior_HorseShoe())
Chains MCMC chain (1000×24×1 Array{Float64, 3}):

Iterations        = 501:1:1500
Number of chains  = 1
Samples per chain = 1000
Wall duration     = 90.76 seconds
Compute duration  = 90.76 seconds
parameters        = τ, λ[1], λ[2], λ[3], λ[4], λ[5], σ, β[1], β[2], β[3], β[4], β[5]
internals         = lp, n_steps, is_accept, acceptance_rate, log_density, hamiltonian_energy, hamiltonian_energy_error, max_hamiltonian_energy_error, tree_depth, numerical_error, step_size, nom_step_size

Summary Statistics
  parameters      mean       std   naive_se      mcse         ess      rhat   ess_per_sec 
      Symbol   Float64   Float64    Float64   Float64     Float64   Float64       Float64 

           τ    0.9361    1.4286     0.0452    0.0594    518.1317    0.9991        5.7086
        λ[1]   10.9980   15.4067     0.4872    0.6976    466.4646    1.0033        5.1394
        λ[2]    0.4934    0.7068     0.0223    0.0227    907.8114    1.0021       10.0020
        λ[3]    1.1991    2.0495     0.0648    0.0643    981.7976    1.0035       10.8172
        λ[4]    1.1391    1.4539     0.0460    0.0650    639.5463    0.9997        7.0463
        λ[5]    1.2285    2.2036     0.0697    0.0733    771.8797    1.0034        8.5043
           σ    0.8506    1.3755     0.0435    0.0594    685.4138    1.0002        7.5517
        β[1]   -1.6771    0.1910     0.0060    0.0064    920.9217    0.9993       10.1464
        β[2]    0.0162    0.0020     0.0001    0.0001   1142.6505    0.9990       12.5894
        β[3]    0.1114    0.0865     0.0027    0.0031    718.5753    0.9992        7.9171
        β[4]    0.0959    0.0153     0.0005    0.0004   1132.1662    0.9993       12.4739
        β[5]    0.1021    0.0118     0.0004    0.0004    869.2085    0.9999        9.5767

Quantiles
  parameters      2.5%     25.0%     50.0%     75.0%     97.5% 
      Symbol   Float64   Float64   Float64   Float64   Float64 

           τ    0.0513    0.2551    0.5591    1.0551    4.1911
        λ[1]    1.1021    3.5425    6.6721   13.0485   47.5960
        λ[2]    0.0281    0.1149    0.2683    0.5840    2.3417
        λ[3]    0.0650    0.3625    0.7063    1.3983    4.6179
        λ[4]    0.1094    0.4109    0.7536    1.3183    4.7938
        λ[5]    0.1194    0.4239    0.7649    1.2889    5.0621
           σ    0.0507    0.2487    0.4977    0.9753    3.1844
        β[1]   -2.0502   -1.8040   -1.6787   -1.5443   -1.3105
        β[2]    0.0122    0.0148    0.0162    0.0176    0.0200
        β[3]   -0.0269    0.0436    0.1048    0.1703    0.2917
        β[4]    0.0684    0.0852    0.0959    0.1058    0.1272
        β[5]    0.0782    0.0946    0.1021    0.1099    0.1258

julia> CRRao.set_rng(StableRNG(7750))
julia> container_cloglog = fit(@formula(Vote ~ Age + Race + Income + Educate), turnout, LogisticRegression(), Cloglog(), Prior_HorseShoe())
Chains MCMC chain (1000×24×1 Array{Float64, 3}):

Iterations        = 501:1:1500
Number of chains  = 1
Samples per chain = 1000
Wall duration     = 94.09 seconds
Compute duration  = 94.09 seconds
parameters        = τ, λ[1], λ[2], λ[3], λ[4], λ[5], σ, β[1], β[2], β[3], β[4], β[5]
internals         = lp, n_steps, is_accept, acceptance_rate, log_density, hamiltonian_energy, hamiltonian_energy_error, max_hamiltonian_energy_error, tree_depth, numerical_error, step_size, nom_step_size

Summary Statistics
  parameters      mean       std   naive_se      mcse         ess      rhat   ess_per_sec 
      Symbol   Float64   Float64    Float64   Float64     Float64   Float64       Float64 

           τ    1.6055   10.8894     0.3444    0.4607    563.7698    1.0009        5.9916
        λ[1]   12.0709   18.6874     0.5909    0.6065    606.1712    1.0007        6.4422
        λ[2]    0.5384    0.9729     0.0308    0.0282    934.6438    0.9991        9.9331
        λ[3]    1.2516    2.0053     0.0634    0.0708    719.1385    1.0009        7.6428
        λ[4]    0.9365    1.0546     0.0333    0.0375    706.7728    0.9990        7.5113
        λ[5]    1.1632    1.8148     0.0574    0.0621    637.0480    1.0002        6.7703
           σ    0.8427    1.4313     0.0453    0.0634    743.6152    1.0109        7.9029
        β[1]   -1.8752    0.1799     0.0057    0.0067    685.7310    0.9990        7.2877
        β[2]    0.0147    0.0018     0.0001    0.0001   1010.6479    0.9990       10.7408
        β[3]    0.1313    0.0869     0.0027    0.0029    635.0589    0.9996        6.7492
        β[4]    0.0770    0.0116     0.0004    0.0004    803.1570    0.9992        8.5357
        β[5]    0.0969    0.0108     0.0003    0.0004    631.0117    0.9994        6.7062

Quantiles
  parameters      2.5%     25.0%     50.0%     75.0%     97.5% 
      Symbol   Float64   Float64   Float64   Float64   Float64 

           τ    0.0679    0.2685    0.5739    1.0915    8.0842
        λ[1]    1.2178    3.5342    6.6865   13.2847   58.1702
        λ[2]    0.0232    0.1050    0.2616    0.6176    2.7919
        λ[3]    0.0779    0.3932    0.7325    1.3764    5.5664
        λ[4]    0.0972    0.3363    0.6103    1.1374    3.4275
        λ[5]    0.1142    0.3990    0.7305    1.2619    4.7179
           σ    0.0319    0.2244    0.4916    0.9191    4.2356
        β[1]   -2.2334   -1.9932   -1.8766   -1.7558   -1.5183
        β[2]    0.0111    0.0134    0.0147    0.0159    0.0180
        β[3]   -0.0100    0.0650    0.1297    0.1920    0.3038
        β[4]    0.0530    0.0690    0.0767    0.0847    0.0999
        β[5]    0.0765    0.0894    0.0966    0.1039    0.1198

julia> CRRao.set_rng(StableRNG(7750))
julia> container_cauchit = fit(@formula(Vote ~ Age + Race + Income + Educate), turnout, LogisticRegression(), Cauchit(), Prior_HorseShoe())
┌ Info: Found initial step size
└   ϵ = 0.8
Chains MCMC chain (1000×24×1 Array{Float64, 3}):

Iterations        = 501:1:1500
Number of chains  = 1
Samples per chain = 1000
Wall duration     = 58.31 seconds
Compute duration  = 58.31 seconds
parameters        = τ, λ[1], λ[2], λ[3], λ[4], λ[5], σ, β[1], β[2], β[3], β[4], β[5]
internals         = lp, n_steps, is_accept, acceptance_rate, log_density, hamiltonian_energy, hamiltonian_energy_error, max_hamiltonian_energy_error, tree_depth, numerical_error, step_size, nom_step_size

Summary Statistics
  parameters      mean       std   naive_se      mcse         ess      rhat   ess_per_sec 
      Symbol   Float64   Float64    Float64   Float64     Float64   Float64       Float64 

           τ    1.0708    1.5386     0.0487    0.0643    593.4742    0.9991       10.1776
        λ[1]   15.3511   26.4777     0.8373    1.3810    350.8906    0.9991        6.0175
        λ[2]    0.6148    0.9366     0.0296    0.0477    424.3585    1.0011        7.2774
        λ[3]    0.9767    1.4798     0.0468    0.0740    452.3447    1.0003        7.7573
        λ[4]    1.6912    2.8264     0.0894    0.1299    409.0444    1.0014        7.0148
        λ[5]    1.2917    1.8591     0.0588    0.0643    601.0381    1.0004       10.3073
           σ    1.0216    1.8927     0.0599    0.0726    636.1415    0.9990       10.9093
        β[1]   -3.0273    0.3875     0.0123    0.0199    451.7525    0.9996        7.7472
        β[2]    0.0297    0.0044     0.0001    0.0002    471.3925    1.0005        8.0840
        β[3]    0.1006    0.1311     0.0041    0.0050    639.1553    0.9990       10.9610
        β[4]    0.2376    0.0382     0.0012    0.0012   1088.5251    0.9992       18.6673
        β[5]    0.1653    0.0243     0.0008    0.0012    505.5200    0.9991        8.6692

Quantiles
  parameters      2.5%     25.0%     50.0%     75.0%     97.5% 
      Symbol   Float64   Float64   Float64   Float64   Float64 

           τ    0.0703    0.3114    0.6561    1.2853    4.6674
        λ[1]    1.1598    3.8901    7.8699   15.9998   76.0001
        λ[2]    0.0306    0.1398    0.3299    0.6663    3.1801
        λ[3]    0.0238    0.2307    0.5136    1.1709    4.5934
        λ[4]    0.1611    0.5298    0.9386    1.7458    7.8814
        λ[5]    0.1182    0.4297    0.8235    1.4823    5.0292
           σ    0.0713    0.3226    0.5813    1.1611    4.1744
        β[1]   -3.7724   -3.2934   -3.0226   -2.7394   -2.3257
        β[2]    0.0216    0.0266    0.0297    0.0327    0.0390
        β[3]   -0.1005    0.0049    0.0767    0.1826    0.4019
        β[4]    0.1614    0.2127    0.2382    0.2638    0.3140
        β[5]    0.1201    0.1472    0.1657    0.1804    0.2148

```
