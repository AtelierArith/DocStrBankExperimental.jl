```
ExtendedKalmanFilter(model::SimModel; <キーワード引数>)
```

[`SimModel`](@ref) `model`を用いて拡張カルマンフィルタを構築します。

[`LinModel`](@ref)および[`NonLinModel`](@ref)の両方がサポートされています。プロセスモデルは[`UnscentedKalmanFilter`](@ref)と同じです。デフォルトでは、拡張モデルのヤコビアン$\mathbf{f̂, ĥ}$は[`ForwardDiff`](@extref ForwardDiff)自動微分を用いて計算されます。この推定器は、`model`のシミュレーションがメモリを割り当てない場合、アロケーションフリーです。

!!! warning
    `MethodError: no method matching (::var"##")(::Vector{ForwardDiff.Dual})`のようなエラーが発生した場合は、[`linearize`](@ref)関数の拡張ヘルプを参照してください。


# 引数

!!! info
    *`強調`*されたキーワード引数は非Unicodeの代替です。


  * `model::SimModel` : 推定のための（決定論的）モデル。
  * `i_ym=1:model.ny` : 測定される`model`の出力インデックス$\mathbf{y^m}$、残りは未測定$\mathbf{y^u}$です。
  * `σP_0=fill(1/model.nx,model.nx)`または*`sigmaP_0`* : 初期推定共分散$\mathbf{P}(0)$の主対角線を、標準偏差ベクトルとして指定します。
  * `σQ=fill(1/model.nx,model.nx)`または*`sigmaQ`* : `model`のプロセスノイズ共分散$\mathbf{Q}$の主対角線を、標準偏差ベクトルとして指定します。
  * `σR=fill(1,length(i_ym))`または*`sigmaR`* : 測定出力のセンサーノイズ共分散$\mathbf{R}$の主対角線を、標準偏差ベクトルとして指定します。
  * `nint_u=0`: 操作入力における未測定の擾乱の確率モデルのための積分器の量（ベクトル）、積分器なしの場合は`nint_u=0`を使用します（拡張ヘルプを参照）。
  * `nint_ym=default_nint(model,i_ym,nint_u)` : 測定出力における未測定の擾乱のための`nint_u`と同じで、積分器なしの場合は`nint_ym=0`を使用します（拡張ヘルプを参照）。
  * `σQint_u=fill(1,sum(nint_u))`または*`sigmaQint_u`* : 操作入力における未測定の擾乱のための$\mathbf{Q_{int_u}}$（積分器で構成）。
  * `σPint_u_0=fill(1,sum(nint_u))`または*`sigmaPint_u_0`* : 操作入力における未測定の擾乱のための$\mathbf{P_{int_u}}(0)$（積分器で構成）。
  * `σQint_ym=fill(1,sum(nint_ym))`または*`sigmaQint_u`* : 測定出力における未測定の擾乱のための$\mathbf{Q_{int_{ym}}}$（積分器で構成）。
  * `σPint_ym_0=fill(1,sum(nint_ym))`または*`sigmaPint_ym_0`* : 測定出力における未測定の擾乱のための$\mathbf{P_{int_{ym}}}(0)$（積分器で構成）。
  * `jacobian=AutoForwardDiff()`: 拡張モデルのヤコビアンのための`AbstractADType`バックエンド、[`DifferentiationInterface` doc](@extref DifferentiationInterface List)を参照してください。
  * `direct=true`: $\mathbf{y^m}$からの直接伝送で構築します（現在の推定器、遅延/予測形式に対して）。

# 例

```jldoctest
julia> model = NonLinModel((x,u,_,_)->0.2x+u, (x,_,_)->-3x, 5.0, 1, 1, 1, solver=nothing);

julia> estim = ExtendedKalmanFilter(model, σQ=[2], σQint_ym=[2], σP_0=[0.1], σPint_ym_0=[0.1])
ExtendedKalmanFilter estimator with a sample time Ts = 5.0 s, NonLinModel and:
 1 manipulated inputs u (0 integrating states)
 2 estimated states x̂
 1 measured outputs ym (1 integrating states)
 0 unmeasured outputs yu
 0 measured disturbances d
```
