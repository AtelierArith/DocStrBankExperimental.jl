```
fit!(
    model::StateSpaceModel;
    filter::KalmanFilter=default_filter(model),
    optimizer::Optimizer=Optimizer(Optim.LBFGS()),
    save_hyperparameter_distribution::Bool=true
)
```

状態空間モデルのパラメータを最大尤度法で推定します。結果として得られる最適なハイパーパラメータと対応する対数尤度はモデル内に保存されます。希望するフィルタメソッド（`UnivariateKalmanFilter`、`ScalarKalmanFilter`など）と[Optim.jl](https://github.com/JuliaNLSolvers/Optim.jl)最適化アルゴリズムを選択できます。

# 例

```jldoctest
julia> model = LocalLevel(rand(100))
LocalLevel

julia> fit!(model)
LocalLevel

julia> model = LocalLinearTrend(LinRange(1, 100, 100) + rand(100))
LocalLinearTrend

julia> fit!(model; optimizer = Optimizer(StateSpaceModels.Optim.NelderMead()))
LocalLinearTrend
```
