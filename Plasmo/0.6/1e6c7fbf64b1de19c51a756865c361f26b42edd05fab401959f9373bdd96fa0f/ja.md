```
@linkconstraint(graph::OptiGraph, expr)
```

式 `expr` で説明されるリンク制約を追加します。

```
@linkconstraint(graph::OptiGraph, ref[i=..., j=..., ...], expr)
```

式 `expr` で説明されるリンク制約のグループを、`i`、`j`、... によってパラメータ化して追加します。

@linkconstraint マクロは `JuMP.@constraint` マクロと同じように機能します。
