```
Expression{T, N, D} <: AbstractExpression{T, N}
```

（実験的）式ツリー（`Node`のような）をカプセル化し、評価とレンダリングのための関連メタデータを持つ高レベルのユーザー向け式タイプを定義します。

# フィールド

  * `tree::N`: 生の式ツリーのルートノード。
  * `metadata::Metadata{D}`: 演算子や変数名など、式の設定のための名前付きタプル。

# コンストラクタ

  * `Expression(tree::AbstractExpressionNode, metadata::NamedTuple)`: フィールドから構築します。
  * `@parse_expression(expr, operators=operators, variable_names=variable_names, node_type=Node)`: 指定されたコンテキストでJulia式を解析し、Expressionオブジェクトを作成します。

# 使用法

このタイプは、エンドユーザーが高レベルで式と対話し、操作することを意図しており、基盤となる式ツリー操作の複雑さを抽象化します。
