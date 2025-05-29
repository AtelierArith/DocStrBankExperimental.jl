```
walk(fn::Function, x)
```

`fn::Function`を`x`に適用する汎用のディスパッチベースのツリーウォーカーで、`Code`ノードタイプ（`Core.ReturnNode`、`Core.GotoNode`、`Core.GotoIfNot`など）に特化しています。ノードのサブフィールドに`fn::Function`を適用し、その結果をノードに再びまとめます。
