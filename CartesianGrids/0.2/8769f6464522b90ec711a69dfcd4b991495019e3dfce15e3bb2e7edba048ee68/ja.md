```
grad(q::Edges{Primal/Dual}) --> EdgeGradient{Dual/Primal,Primal/Dual}
```

プライマルまたはデュアルエッジデータ `q` の離散勾配を評価します。この操作は、Grad型のオブジェクトを作成し、`*` で適用することでも実行できます。
