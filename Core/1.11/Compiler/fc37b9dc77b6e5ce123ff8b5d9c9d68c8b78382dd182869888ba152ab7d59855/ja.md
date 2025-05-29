```
is_identity_free_argtype(argtype) -> Bool
```

`argtype`オブジェクトがアイデンティティフリーである場合、つまりこの型またはそのフィールドを通じて到達可能な型が内容ベースのアイデンティティを持たない場合に`true`を返します（`Base.isidentityfree`を参照）。このクエリは特に`adjust_effects`のために設計されており、戻り値の型が`is_identity_free_argtype`であるときに、分析されたコールグラフ内の可変アロケーションによって汚染された`:consistent`効果プロパティを洗練させることを可能にし、アロケートされた可変オブジェクトが決して返されないことを保証します。
