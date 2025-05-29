インプレースメソッド[`bilqr!`](@ref)のためのワークスペース。

このワークスペースを初期化するために使用できる外部コンストラクタは次のとおりです：

```
workspace = BilqrWorkspace(m, n, S)
workspace = BilqrWorkspace(A, b)
workspace = BilqrWorkspace(kc::KrylovConstructor)
```
