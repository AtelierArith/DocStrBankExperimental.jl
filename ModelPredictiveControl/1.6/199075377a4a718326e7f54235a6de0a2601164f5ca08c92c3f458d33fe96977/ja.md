```
KalmanFilter(model::LinModel; <キーワード引数>)
```

[`LinModel`](@ref) `model`を用いて時間変化するカルマンフィルタを構築します。

プロセスモデルは[`SteadyKalmanFilter`](@ref)と同一です。行列$\mathbf{P̂}$は、`model`の状態の推定誤差共分散で、確率的なもの（`nint_u`および`nint_ym`で指定）を増強したものです。3つのキーワード引数が初期値を指定します。$\mathbf{P̂}_{-1}(0) = \mathrm{diag}\{ \mathbf{P}(0), \mathbf{P_{int_{u}}}(0),  \mathbf{P_{int_{ym}}}(0) \}$。初期状態推定$\mathbf{x̂}_{-1}(0)$は、[`setstate!`](@ref)で手動で指定するか、[`initstate!`](@ref)で自動的に指定できます。この推定器はアロケーションフリーです。

# 引数

!!! info
    *`強調`*されたキーワード引数は非Unicodeの代替です。


  * `model::LinModel` : （決定論的）推定のためのモデル。
  * `i_ym=1:model.ny` : 測定される`model`の出力インデックス$\mathbf{y^m}$、残りは未測定の$\mathbf{y^u}$です。
  * `σP_0=fill(1/model.nx,model.nx)`または*`sigmaP_0`* : 初期推定共分散$\mathbf{P}(0)$の主対角線、標準偏差ベクトルとして指定。
  * `σQ=fill(1/model.nx,model.nx)`または*`sigmaQ`* : `model`のプロセスノイズ共分散$\mathbf{Q}$の主対角線、標準偏差ベクトルとして指定。
  * `σR=fill(1,length(i_ym))`または*`sigmaR`* : 測定出力のセンサーノイズ共分散$\mathbf{R}$の主対角線、標準偏差ベクトルとして指定。
  * `nint_u=0`: 操作入力の未測定の擾乱に対する確率モデルのための積分器の量（ベクトル）、積分器なしの場合は`nint_u=0`を使用。
  * `nint_ym=default_nint(model,i_ym,nint_u)` : 測定出力の未測定の擾乱に対する`nint_u`と同様、積分器なしの場合は`nint_ym=0`を使用。
  * `σQint_u=fill(1,sum(nint_u))`または*`sigmaQint_u`* : 操作入力の未測定の擾乱に対する$\mathbf{Q_{int_u}}$（積分器で構成）。
  * `σPint_u_0=fill(1,sum(nint_u))`または*`sigmaPint_u_0`* : 操作入力の未測定の擾乱に対する$\mathbf{P_{int_u}}(0)$（積分器で構成）。
  * `σQint_ym=fill(1,sum(nint_ym))`または*`sigmaQint_u`* : 測定出力の未測定の擾乱に対する$\mathbf{Q_{int_{ym}}}$（積分器で構成）。
  * `σPint_ym_0=fill(1,sum(nint_ym))`または*`sigmaPint_ym_0`* : 測定出力の未測定の擾乱に対する$\mathbf{P_{int_{ym}}}(0)$（積分器で構成）。
  * `direct=true`: $\mathbf{y^m}$からの直接伝送で構築（現在の推定器、遅延/予測形式に対して）。

# 例

```jldoctest
julia> model = LinModel([tf(3, [30, 1]); tf(-2, [5, 1])], 0.5);

julia> estim = KalmanFilter(model, i_ym=[2], σR=[1], σP_0=[100, 100], σQint_ym=[0.01])
KalmanFilter estimator with a sample time Ts = 0.5 s, LinModel and:
 1 manipulated inputs u (0 integrating states)
 3 estimated states x̂
 1 measured outputs ym (1 integrating states)
 1 unmeasured outputs yu
 0 measured disturbances d
```
