インプレースメソッド[`fgmres!`](@ref)のためのワークスペース。

このワークスペースを初期化するために使用できる外部コンストラクタは次のとおりです：

```
workspace = FgmresWorkspace(m, n, S; memory = 20)
workspace = FgmresWorkspace(A, b; memory = 20)
workspace = FgmresWorkspace(kc::KrylovConstructor; memory = 20)
```

`memory`は、指定された値が`n`より大きい場合、`n`に設定されます。
