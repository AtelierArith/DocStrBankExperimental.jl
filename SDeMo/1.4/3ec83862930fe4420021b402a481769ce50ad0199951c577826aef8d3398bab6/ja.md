```
variables!(model::AbstractSDM, ::Type{T}, folds::Vector{Tuple{Vector{Int}, Vector{Int}}}; included=Int[], optimality=mcc, verbose::Bool=false, bagfeatures::Bool=false, kwargs...) where {T <: VariableSelectionStrategy}
```

選択戦略に基づいて変数選択を行い、交差検証のための `folds` を指定することができます。省略した場合、これは k-分割にデフォルト設定されます。

モデルは、トレーニング後に最適な変数のセットで再トレーニングされます。

**キーワード**:

  * `included` (`Int[]`)、モデルに必ず含める必要がある変数のリスト
  * `optimality` (`mcc`)、各ラウンドの変数選択で最適化する指標
  * `verbose` (`false`)、各ラウンドの変数選択後にパフォーマンスを返すかどうか
  * `bagfeatures` (`false`)、均質なアンサンブル内の各モデルで `bagfeatures!` を呼び出すかどうか
  * その他のキーワードは `train!` および `crossvalidate` に渡されます

**重要な注意事項**:

1. 含まれる変数のプールで `bagfeatures` を使用する場合、それらは常に全体のモデルに存在しますが、アンサンブルの各モデルに必ずしも存在するわけではありません。
2. `VarianceInflationFactor` を使用する場合、VIF が閾値を超えていても、パフォーマンスが低下するモデルを生成することになる場合は変数選択が停止します – `variables!` を使用することで *常に* より良いモデルが得られます。
