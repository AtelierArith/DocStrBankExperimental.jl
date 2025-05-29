```
metropolis(ll::Function(θ), R::Int, θ₀::Vector, draw::Function(θ) = naive_sampler(θ₀))
```

マルジナルメトロポリス（-ハスティングス）アルゴリズムを使用してMCMCサンプリングを実行します。`draw = θ -> θ'`は古いパラメータベクトルに基づいて新しいパラメータベクトルをサンプリングします。分布は対称でなければなりません。例えば、ガウス分布です。`R`は反復回数です。`log_likelihood_fun`を参照してください。

# 例:

```julia
filter_from_parameters(θ) = ParticleFilter(N, dynamics, measurement, MvNormal(n,exp(θ[1])), MvNormal(p,exp(θ[2])), d0)
priors = [Normal(0,0.1),Normal(0,0.1)]
ll     = log_likelihood_fun(filter_from_parameters,priors,u,y,1)
θ₀ = log.([1.,1.]) # 初期点
draw = θ -> θ .+ rand(MvNormal(0.1ones(2))) # 新しいパラメータを提案する関数（対称である必要があります）
burnin = 200 # スレッド呼び出しを使用する場合、バーニン反復の数を指定します
# @time theta, lls = metropolis(ll, 2000, θ₀, draw) # シングルスレッドで実行
# thetam = reduce(hcat, theta)'
@time thetalls = LowLevelParticleFilters.metropolis_threaded(burnin, ll, 5000, θ₀, draw) # すべてのスレッドで実行し、(2000-burnin)*nthreads()サンプルを提供します
histogram(exp.(thetalls[:,1:2]), layout=3)
plot!(thetalls[:,3], subplot=3) # スレッド呼び出しの場合、対数尤度は最後の列にあります
```
