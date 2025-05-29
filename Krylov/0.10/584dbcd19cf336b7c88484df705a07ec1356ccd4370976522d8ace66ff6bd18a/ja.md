インプレースメソッド[`gpmr!`](@ref)のためのワークスペース。

このワークスペースを初期化するために使用できる外部コンストラクタは次のとおりです：

```
workspace = GpmrWorkspace(m, n, S; memory = 20)
workspace = GpmrWorkspace(A, b; memory = 20)
workspace = GpmrWorkspace(kc::KrylovConstructor; memory = 20)
```

`memory`は、指定された値が`n + m`より大きい場合、`n + m`に設定されます。
