```julia
fit(formula::FormulaTerm,data::DataFrame,modelClass::NegBinomRegression,prior::Prior_HorseShoe,sim_size::Int64 = 1000)
```

入力データに対してHorseShoe事前分布を用いたベイズ負の二項回帰モデルを適合させます。

# 例

```julia-repl
julia> using CRRao, RDatasets, StableRNGs, StatsPlots, StatsModels
julia> sanction = dataset("Zelig", "sanction");
julia> CRRao.set_rng(StableRNG(123))
julia> container = fit(@formula(Num ~ Target + Coop + NCost), sanction, NegBinomRegression(), Prior_HorseShoe())
┌ Info: Found initial step size
└   ϵ = 0.05
Chains MCMC chain (1000×26×1 Array{Float64, 3}):

Iterations        = 501:1:1500
Number of chains  = 1
Samples per chain = 1000
Wall duration     = 3.74 seconds
Compute duration  = 3.74 seconds
parameters        = τ, λ[1], λ[2], λ[3], λ[4], λ[5], λ[6], σ, β[1], β[2], β[3], β[4], β[5], β[6]
internals         = lp, n_steps, is_accept, acceptance_rate, log_density, hamiltonian_energy, hamiltonian_energy_error, max_hamiltonian_energy_error, tree_depth, numerical_error, step_size, nom_step_size

Summary Statistics
  parameters      mean       std   naive_se      mcse        ess      rhat   ess_per_sec 
      Symbol   Float64   Float64    Float64   Float64    Float64   Float64       Float64 

           τ    0.4838    0.4157     0.0131    0.0308   173.3105    1.0086       46.3397
        λ[1]    1.5987    2.6514     0.0838    0.1408   419.8568    1.0017      112.2612
        λ[2]    0.5508    0.8382     0.0265    0.0342   585.4782    1.0002      156.5450
        λ[3]    2.0960    2.2974     0.0726    0.1275   359.7626    1.0205       96.1932
        λ[4]    0.9183    1.2790     0.0404    0.0631   447.9905    1.0010      119.7835
        λ[5]    2.5239    3.4791     0.1100    0.1755   369.0944    1.0009       98.6883
        λ[6]    0.7963    3.1672     0.1002    0.1031   906.7498    0.9990      242.4465
           σ    2.3692    0.5405     0.0171    0.0335   160.7206    1.0116       42.9734
        β[1]   -0.6991    0.4640     0.0147    0.0403    74.1265    1.0119       19.8199
        β[2]   -0.0675    0.1221     0.0039    0.0084   157.2105    1.0021       42.0349
        β[3]    0.9701    0.1417     0.0045    0.0129    45.9995    1.0279       12.2993
        β[4]   -0.0838    0.3660     0.0116    0.0201   289.6569    1.0192       77.4484
        β[5]    1.2784    0.3110     0.0098    0.0193   190.0338    1.0033       50.8112
        β[6]   -0.0028    0.2110     0.0067    0.0169    95.8876    1.0065       25.6384

Quantiles
  parameters      2.5%     25.0%     50.0%     75.0%     97.5% 
      Symbol   Float64   Float64   Float64   Float64   Float64 

           τ    0.0879    0.2295    0.3679    0.5927    1.4404
        λ[1]    0.0227    0.4536    0.9371    1.8603    6.6116
        λ[2]    0.0162    0.1229    0.2742    0.6572    2.5594
        λ[3]    0.2818    0.9145    1.5319    2.3517    7.9027
        λ[4]    0.0562    0.2805    0.5363    1.0203    4.5210
        λ[5]    0.3047    0.9296    1.5168    2.8306   10.3197
        λ[6]    0.0241    0.1982    0.3462    0.8242    3.1959
           σ    1.5715    1.9489    2.3025    2.6799    3.6985
        β[1]   -1.6118   -1.0219   -0.7054   -0.3626    0.0332
        β[2]   -0.2998   -0.1666   -0.0557    0.0150    0.1638
        β[3]    0.7268    0.8657    0.9770    1.0755    1.2406
        β[4]   -0.9419   -0.2720   -0.0234    0.1072    0.6187
        β[5]    0.6108    1.0708    1.2936    1.5336    1.8016
        β[6]   -0.3937   -0.1448   -0.0029    0.1130    0.4378
```
