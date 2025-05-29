インプレースメソッド[`block_gmres!`](@ref)のためのワークスペース。

このワークスペースを初期化するために使用できる外部コンストラクタは次のとおりです：

```
workspace = BlockGmresWorkspace(m, n, p, SV, SM; memory = 5)
workspace = BlockGmresWorkspace(A, B; memory = 5)
```

`memory`は、指定された値が`div(n,p)`より大きい場合、`div(n,p)`に設定されます。
