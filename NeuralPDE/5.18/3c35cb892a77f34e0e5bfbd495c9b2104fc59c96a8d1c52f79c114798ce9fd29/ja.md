```
PINOODE(chain,
    opt,
    bounds;
    init_params = nothing,
    strategy = nothing
    kwargs...)
```

物理に基づいたニューラルオペレーターを使用してパラメトリック常微分方程式を解くためのアルゴリズムで、パラメータ化された `ODEProblem` のソルバーとして使用されます。

## 位置引数

  * `chain`: `AbstractLuxLayer` または `Flux.Chain` として定義されたニューラルネットワークアーキテクチャ。                `Flux.Chain` は `adapt(FromFluxAdaptor(false, false), chain)` を使用して `Lux` に変換されます。
  * `opt`: ニューラルネットワークをトレーニングするためのオプティマイザー。
  * `bounds`: パラメトリックODEのパラメータの境界を含む辞書。
  * `number_of_parameters`: パラメータ境界内のトレーニングセットのポイント数。

## キーワード引数

  * `init_params`: ニューラルネットワークの初期パラメータ。デフォルトでは `nothing` であり、したがってニューラルネットワークライブラリによって提供されるランダム初期化が使用されます。
  * `strategy`: ニューラルネットワークのトレーニング戦略。
  * `additional_loss`: デフォルトの損失関数に追加される追加の損失関数。例えば、データに対するトレーニングを追加します。
  * `kwargs`: 追加のキーワード引数は、Optimization.jl の `solve` 呼び出しにスプラットされます。

## 参考文献

  * Sifan Wang "物理に基づいたDeepOnetsを用いたパラメトリック偏微分方程式の解演算子の学習"
  * Zongyi Li "偏微分方程式を学習するための物理に基づいたニューラルオペレーター"
