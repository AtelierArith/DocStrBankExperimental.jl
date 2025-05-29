```
getnormal(iv::InterfaceValues, qp::Int; here::Bool=true)
```

インターフェース上の quadrature point `qp` における法線ベクトルを返します。`here = true`（デフォルト）の場合は「ここ」の要素に対する外向き法線が返され、それ以外の場合は「そこ」の要素に対する外向き法線が返されます。
