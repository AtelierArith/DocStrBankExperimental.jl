```julia
struct TransformInfo
```

パラメータを抽出するためのトレースの引数を含みます。 'TraceTransform' を構築するために使用されます。

# フィールド

  * `chains::Vector{Int64}`: 出力診断に使用されるチェインインデックス。
  * `algorithms::Vector{Int64}`: 出力診断に使用されるアルゴリズムインデックス。
  * `burnin::Int64`: 出力診断が行われる前のバーニンステップの数。
  * `thinning::Int64`: 2つの連続サンプルの間に設定されるステップの数。
  * `maxiterations::Int64`: 各チェインのために収集される最大反復回数。
  * `effective_iterations::StepRange{Int64, Int64}`: 有効サンプルのインデックスのための StepRange。
