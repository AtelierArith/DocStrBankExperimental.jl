インプレースメソッド[`minres_qlp!`](@ref)のためのワークスペース。

以下の外部コンストラクタを使用して、このワークスペースを初期化できます：

```
workspace = MinresQlpWorkspace(m, n, S)
workspace = MinresQlpWorkspace(A, b)
workspace = MinresQlpWorkspace(kc::KrylovConstructor)
```
