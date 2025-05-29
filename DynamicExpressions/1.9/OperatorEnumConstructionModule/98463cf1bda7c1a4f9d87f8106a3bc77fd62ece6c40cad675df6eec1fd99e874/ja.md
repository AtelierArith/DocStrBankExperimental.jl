```
OperatorEnum(; binary_operators=[], unary_operators=[],
               define_helper_functions::Bool=true,
               empty_old_operators::Bool=true)
```

`OperatorEnum`オブジェクトを構築し、可能な式を定義します。これにより、`AbstractExpressionNode`タイプの演算子が再定義され、`show`、`print`、および`(::AbstractExpressionNode)(X)`も再定義されます。また、`Zygote.jl`を使用して自動的に導関数を計算します。

# 引数

  * `binary_operators::Vector{Function}`: 各々が二項演算子である関数のベクトル。
  * `unary_operators::Vector{Function}`: 各々が単項演算子である関数のベクトル。
  * `define_helper_functions::Bool=true`: ノードタイプを作成および評価するためのヘルパー関数を定義するかどうか。事前コンパイルを行う際にはこれをオフにしてください。これらはパッケージが機能するために*必要*ではなく、純粋に便利のためのものです。
  * `empty_old_operators::Bool=true`: 古い演算子をクリアするかどうか。
