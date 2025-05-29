```julia
fit(formula::FormulaTerm,data::DataFrame,modelClass::LinearRegression,prior::Prior_HorseShoe,sim_size::Int64 = 1000)
```

入力データに対してHorseShoe事前分布を用いたベイズ線形回帰モデルを適合させます。

# 例

```julia-repl
julia> using CRRao, RDatasets, StableRNGs, StatsPlots, StatsModels
julia> df = dataset("datasets", "mtcars");                                                                                                 
julia> CRRao.set_rng(StableRNG(123));
julia> container = fit(@formula(MPG ~ HP + WT + Gear), df, LinearRegression(), Prior_HorseShoe())
┌ Info: Found initial step size
└   ϵ = 0.00078125
Chains MCMC chain (1000×22×1 Array{Float64, 3}):

Iterations        = 501:1:1500
Number of chains  = 1
Samples per chain = 1000
Wall duration     = 1.25 seconds
Compute duration  = 1.25 seconds
parameters        = τ, λ[1], λ[2], λ[3], λ[4], σ, β[1], β[2], β[3], β[4]
internals         = lp, n_steps, is_accept, acceptance_rate, log_density, hamiltonian_energy, hamiltonian_energy_error, max_hamiltonian_energy_error, tree_depth, numerical_error, step_size, nom_step_size

Summary Statistics
  parameters      mean        std   naive_se      mcse        ess      rhat   ess_per_sec 
      Symbol   Float64    Float64    Float64   Float64    Float64   Float64       Float64 

           τ    1.5261     1.6534     0.0523    0.0828   436.8230    0.9997      350.8618
        λ[1]   24.2059   136.8466     4.3275    6.3344   451.4820    0.9999      362.6362
        λ[2]    0.3444     0.5997     0.0190    0.0200   781.1539    0.9993      627.4329
        λ[3]    2.1643     4.5499     0.1439    0.2182   389.8004    1.0002      313.0927
        λ[4]    1.1324     2.6245     0.0830    0.1221   493.6815    1.0004      396.5314
           σ    2.6141     0.3517     0.0111    0.0165   460.6283    0.9993      369.9826
        β[1]   31.8252     4.8143     0.1522    0.3050   179.8377    1.0103      144.4479
        β[2]   -0.0372     0.0110     0.0003    0.0006   294.1383    1.0042      236.2557
        β[3]   -3.0585     0.9423     0.0298    0.0595   178.2695    1.0099      143.1883
        β[4]    0.9625     0.8550     0.0270    0.0523   198.7195    1.0077      159.6141

Quantiles
  parameters      2.5%     25.0%     50.0%     75.0%     97.5% 
      Symbol   Float64   Float64   Float64   Float64   Float64 

           τ    0.2477    0.6709    1.0774    1.8008    5.6212
        λ[1]    1.6288    5.3511    9.8538   20.7166   83.5487
        λ[2]    0.0059    0.0418    0.1257    0.3737    2.2231
        λ[3]    0.2183    0.7248    1.2997    2.4004    8.0168
        λ[4]    0.0437    0.2932    0.6094    1.1282    4.8634
           σ    2.0417    2.3731    2.5859    2.8043    3.3936
        β[1]   20.9216   29.1543   32.3072   35.1725   39.4603
        β[2]   -0.0597   -0.0442   -0.0369   -0.0300   -0.0171
        β[3]   -4.7741   -3.6626   -3.1250   -2.5222   -1.0155
        β[4]   -0.3640    0.3357    0.8594    1.4728    2.8541

julia> plot(container.chain)
```
