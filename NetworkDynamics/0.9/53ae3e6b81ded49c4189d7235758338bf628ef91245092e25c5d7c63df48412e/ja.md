```
ff_to_constraint(v::VertexModel)
```

フィードフォワードを持つ`VertexModel` `v`を受け取り、すべての代数出力状態を内部状態に変換します。これは代数制約`0 = out - g(...)`を定義することによって行われます。新しい出力関数は、拡張された内部状態ベクトルへの単なる[`StateMask`](@ref)です。

変換された`VertexModel`を返します。
