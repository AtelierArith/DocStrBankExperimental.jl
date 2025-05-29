SamplingOp(pattern::Array{Int}, shape::Tuple)

`pattern`で示された位置のベクトル要素のみを返す`LinearOperator`を構築します。

# 引数

  * `pattern::Array{Int}` - サンプリングするインデックス
  * `shape::Tuple`        - サンプリングする配列のサイズ
