```
loglikelihood(param, data, model)
```

さまざまなタイプのデータとモデルの対数尤度を計算します。

# 引数

  * `param`: モデルパラメータ。
  * `data`: データで、さまざまなタイプ（例：`AbstractHistogramData`、`AbstractTraceData`、`TraceData`、`TraceRNAData`）を持つことができます。
  * `model`: モデルで、さまざまなタイプ（例：`AbstractGmodel`、`GRSMcoupledmodel`、`AbstractGRSMmodel`、`GRSMhierarchicalmodel`）を持つことができます。

# 説明

この関数は、異なるタイプのデータとモデルの対数尤度を計算します。ヒストグラムデータ、トレースデータ、カップルモデル、および階層モデルをサポートしています。特定の計算方法は、提供された`data`と`model`のタイプに依存します。

# メソッド

  * `loglikelihood(param, data::AbstractHistogramData, model::AbstractGmodel)`: すべてのデータの対数尤度と予測ヒストグラム対数尤度のベクトルを返します。
  * `loglikelihood(param, data::AbstractTraceData, model::AbstractGmodel)`: 組み合わされた時系列トレースと各トレースの対数尤度を返します。
  * `loglikelihood(param, data::TraceData, model::GRSMcoupledmodel)`: カップルモデルの対数尤度を返します。
  * `loglikelihood(param, data::TraceRNAData, model::AbstractGRSMmodel)`: 時系列トレースとmRNA FISH定常状態ヒストグラムの対数尤度を返します。
  * `loglikelihood(param, data::AbstractTraceData, model::GRSMhierarchicalmodel)`: 階層モデルの対数尤度を返します。

# 戻り値

  * `Float64`: 組み合わされた時系列トレースと各トレースの対数尤度。
  * `Tuple{Float64, Vector{Float64}}`: すべてのデータの対数尤度と予測ヒストグラム対数尤度のベクトル。

# 規約

  * このコードベースのすべてのloglikelihood関数は、対数尤度（高い方が良い）を返し、負の対数尤度は返しません。
