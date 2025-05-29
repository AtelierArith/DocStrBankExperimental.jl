```
AbstractExpression{T,N}
```

（実験的）ユーザー向けの式タイプのための抽象型で、値型 `T` に対して操作する生の式ツリーと、式を評価およびレンダリングするための関連メタデータの両方を含みます。

インターフェースの実装の完全な説明や、正確性を検証するためのテストについては、[`ExpressionInterface`](@ref DynamicExpressions.InterfacesModule.ExpressionInterface)を参照してください。

`@parse_expression`を使用したい場合は、次のように解析の動作をカスタマイズすることもできます。

  * `parse_leaf`
