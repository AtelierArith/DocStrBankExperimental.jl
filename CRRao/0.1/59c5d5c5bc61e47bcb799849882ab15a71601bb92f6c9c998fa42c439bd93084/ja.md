```julia
fit(formula::FormulaTerm,data::DataFrame,modelClass::PoissonRegression,prior::Prior_HorseShoe,sim_size::Int64 = 1000)
```

入力データに対してホースシュー事前分布を用いたベイズポアソン回帰モデルをフィットします。

# 例

```julia-repl
julia> using CRRao, RDatasets, StableRNGs, StatsModels
julia> sanction = dataset("Zelig", "sanction");
julia> CRRao.set_rng(StableRNG(123))
julia> container = fit(@formula(Num ~ Target + Coop + NCost), sanction, PoissonRegression(), Prior_HorseShoe())
┌ Info: Found initial step size
└   ϵ = 0.025
Chains MCMC chain (1000×25×1 Array{Float64, 3}):

Iterations        = 501:1:1500
Number of chains  = 1
Samples per chain = 1000
Wall duration     = 4.1 seconds
Compute duration  = 4.1 seconds
parameters        = τ, λ[1], λ[2], λ[3], λ[4], λ[5], λ[6], β[1], β[2], β[3], β[4], β[5], β[6]
internals         = lp, n_steps, is_accept, acceptance_rate, log_density, hamiltonian_energy, hamiltonian_energy_error, max_hamiltonian_energy_error, tree_depth, numerical_error, step_size, nom_step_size

Summary Statistics
  parameters      mean       std   naive_se      mcse        ess      rhat   ess_per_sec 
      Symbol   Float64   Float64    Float64   Float64    Float64   Float64       Float64 

           τ    1.0968    0.7202     0.0228    0.0309   495.7869    1.0052      120.9531
        λ[1]    3.1027    3.8858     0.1229    0.1974   409.1763    1.0058       99.8234
        λ[2]    0.7001    1.3791     0.0436    0.0493   705.5283    0.9990      172.1220
        λ[3]    2.3944    3.2504     0.1028    0.1437   501.7931    1.0042      122.4184
        λ[4]    0.9352    1.7652     0.0558    0.0791   582.3219    1.0034      142.0644
        λ[5]    3.3768    6.5014     0.2056    0.2544   610.2202    1.0001      148.8705
        λ[6]    1.2451    2.2218     0.0703    0.1224   350.1233    1.0004       85.4168
        β[1]   -1.7490    0.2761     0.0087    0.0128   431.8956    0.9998      105.3661
        β[2]    0.1184    0.0706     0.0022    0.0034   468.3049    0.9991      114.2486
        β[3]    1.1297    0.0571     0.0018    0.0025   564.1507    1.0001      137.6313
        β[4]   -0.2202    0.2117     0.0067    0.0063   733.3563    0.9997      178.9110
        β[5]    1.7059    0.1021     0.0032    0.0035   909.1702    0.9994      221.8029
        β[6]    0.3723    0.1751     0.0055    0.0063   559.1851    0.9990      136.4199

Quantiles
  parameters      2.5%     25.0%     50.0%     75.0%     97.5% 
      Symbol   Float64   Float64   Float64   Float64   Float64 

           τ    0.2712    0.6245    0.8979    1.3762    2.9053
        λ[1]    0.5269    1.2258    2.0465    3.3300   14.0447
        λ[2]    0.0259    0.1688    0.3584    0.7633    3.2174
        λ[3]    0.3468    0.8696    1.4059    2.5462   12.1721
        λ[4]    0.0374    0.2091    0.5065    0.9706    4.2828
        λ[5]    0.4982    1.2214    1.9925    3.4033   14.6181
        λ[6]    0.1048    0.3658    0.6567    1.2087    7.2850
        β[1]   -2.3007   -1.9417   -1.7414   -1.5683   -1.2303
        β[2]   -0.0040    0.0678    0.1152    0.1684    0.2634
        β[3]    1.0235    1.0905    1.1299    1.1665    1.2456
        β[4]   -0.6741   -0.3592   -0.2024   -0.0517    0.1380
        β[5]    1.4992    1.6387    1.7051    1.7718    1.9102
        β[6]    0.0305    0.2485    0.3763    0.4911    0.7002
julia> using StatsPlots
julia> plot(container.chain)
```
