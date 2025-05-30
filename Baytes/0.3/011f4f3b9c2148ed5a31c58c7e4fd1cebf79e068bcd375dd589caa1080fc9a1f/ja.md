```julia
struct TraceTransform{T<:ModelWrappers.Tagged, P}
```

トレースからパラメータを抽出するための引数を含みます。

# フィールド

  * `tagged::ModelWrappers.Tagged`: 出力情報が印刷されるパラメータを含みます。
  * `paramnames::Any`: タグ付きモデルパラメータに基づくパラメータ名。
  * `chains::Vector{Int64}`: 出力診断に使用されるチェインインデックス。
  * `algorithms::Vector{Int64}`: 出力診断に使用されるアルゴリズムインデックス。
  * `burnin::Int64`: 出力診断が行われる前のバーニンステップの数。
  * `thinning::Int64`: 2つの連続サンプルの間に設定されるステップの数。
  * `maxiterations::Int64`: 各チェインのために収集される最大反復回数。
  * `effective_iterations::StepRange{Int64, Int64}`: 有効サンプルのインデックスのためのStepRange。
