インプレースメソッド[`dqgmres!`](@ref)のためのワークスペース。

次の外部コンストラクタを使用して、このワークスペースを初期化できます：

```
workspace = DqgmresWorkspace(m, n, S; memory = 20)
workspace = DqgmresWorkspace(A, b; memory = 20)
workspace = DqgmresWorkspace(kc::KrylovConstructor; memory = 20)
```

`memory`は、指定された値が`n`より大きい場合、`n`に設定されます。
