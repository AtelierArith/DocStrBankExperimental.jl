```
MutationWeights(;kws...) <: AbstractMutationWeights
```

これは、異なる突然変異が発生する頻度を定義します。これらの重みは、初期化後に合計が1.0になるように正規化されます。

# 引数

  * `mutate_constant::Float64`: 定数を突然変異させる頻度。
  * `mutate_operator::Float64`: 演算子を突然変異させる頻度。
  * `swap_operands::Float64`: 二項演算子のオペランドを入れ替える頻度。
  * `rotate_tree::Float64`: ランダムなノードでツリーの回転を行う頻度。
  * `add_node::Float64`: ツリーにノードを追加する頻度。
  * `insert_node::Float64`: ツリーにノードを挿入する頻度。
  * `delete_node::Float64`: ツリーからノードを削除する頻度。
  * `simplify::Float64`: ツリーを簡略化する頻度。
  * `randomize::Float64`: ランダムなツリーを作成する頻度。
  * `do_nothing::Float64`: 何もしない頻度。
  * `optimize::Float64`: 突然変異としてツリー内の定数を最適化する頻度。これは、すべての個体の反復の最後に実行される`optimizer_probability`とは異なります。
  * `form_connection::Float64`: **`GraphNode`にのみ使用され、通常の`Node`には使用されません**。そうでない場合、これは自動的に0.0に設定されます。2つのノード間に接続を形成する頻度。
  * `break_connection::Float64`: **`GraphNode`にのみ使用され、通常の`Node`には使用されません**。そうでない場合、これは自動的に0.0に設定されます。2つのノード間の接続を切断する頻度。

# 参照

  * [`AbstractMutationWeights`](@ref SymbolicRegression.CoreModule.MutationWeightsModule.AbstractMutationWeights): カスタム突然変異重みタイプを定義するために使用します。
