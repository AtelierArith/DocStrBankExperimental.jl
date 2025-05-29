インプレースメソッド[`cgls!`](@ref)のためのワークスペース。

以下の外部コンストラクタを使用して、このワークスペースを初期化できます：

```
workspace = CglsWorkspace(m, n, S)
workspace = CglsWorkspace(A, b)
workspace = CglsWorkspace(kc::KrylovConstructor)
```
