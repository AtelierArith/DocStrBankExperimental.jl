インプレースメソッド[`minres!`](@ref)のためのワークスペース。

次の外部コンストラクタを使用して、このワークスペースを初期化できます：

```
workspace = MinresWorkspace(m, n, S; window = 5)
workspace = MinresWorkspace(A, b; window = 5)
workspace = MinresWorkspace(kc::KrylovConstructor; window = 5)
```
