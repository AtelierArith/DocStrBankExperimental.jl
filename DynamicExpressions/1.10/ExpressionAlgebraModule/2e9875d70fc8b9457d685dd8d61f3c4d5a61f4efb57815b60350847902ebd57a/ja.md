```
@declare_expression_operator(op, arity)
```

`AbstractExpression` 型の演算子関数を宣言します。

このマクロは、与えられた演算子 `op` に対して、`AbstractExpression` 引数で動作するメソッドを生成します。`arity` パラメータは、演算子が単項（1）か二項（2）かを指定します。

# 引数

  * `op`: 宣言する演算子（例: `Base.sin`, `Base.:+`）。
  * `arity`: 演算子が取る引数の数（単項の場合は1、二項の場合は2）。
