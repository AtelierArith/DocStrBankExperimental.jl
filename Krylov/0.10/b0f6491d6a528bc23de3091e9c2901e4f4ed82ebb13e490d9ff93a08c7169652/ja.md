インプレースメソッド[`lsqr!`](@ref)のためのワークスペース。

このワークスペースを初期化するために使用できる外部コンストラクタは次のとおりです：

```
workspace = LsqrWorkspace(m, n, S)
workspace = LsqrWorkspace(A, b)
workspace = LsqrWorkspace(kc::KrylovConstructor)
```
