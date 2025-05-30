```
Luenberger(
    model::LinModel; 
    i_ym = 1:model.ny, 
    nint_u  = 0,
    nint_ym = default_nint(model, i_ym),
    poles = 1e-3*(1:(model.nx + sum(nint_u) + sum(nint_ym))) .+ 0.5,
    direct = true
)
```

[`LinModel`](@ref) `model`を用いてルエンバーガーオブザーバを構築します。

`i_ym`は、測定されたモデル出力インデックス$\mathbf{y^m}$を提供し、残りは未測定の$\mathbf{y^u}$です。`model`の行列は、積分器の数`nint_u`と`nint_ym`によって指定される確率モデルで拡張されます（詳細は[`SteadyKalmanFilter`](@ref)の拡張ヘルプを参照）。引数`poles`は、オブザーバの極/固有値を指定する`model.nx + sum(nint_u) + sum(nint_ym)`要素のベクトルです（デフォルトでは$z=0.5$付近）。`direct=true`の場合、オブザーバは$\mathbf{y^m}$からの直接伝送で構築されます（遅延/予測形式とは対照的に、現在のオブザーバとも呼ばれます）。このメソッドは、[`place`](@extref ControlSystemsBase.place)関数を使用してオブザーバゲイン`K̂`を計算します。この推定器は、アロケーションフリーです。

# 例

```jldoctest
julia> model = LinModel([tf(3, [30, 1]); tf(-2, [5, 1])], 0.5);

julia> estim = Luenberger(model, nint_ym=[1, 1], poles=[0.61, 0.62, 0.63, 0.64])
Luenberger estimator with a sample time Ts = 0.5 s, LinModel and:
 1 manipulated inputs u (0 integrating states)
 4 estimated states x̂
 2 measured outputs ym (2 integrating states)
 0 unmeasured outputs yu
 0 measured disturbances d
```
