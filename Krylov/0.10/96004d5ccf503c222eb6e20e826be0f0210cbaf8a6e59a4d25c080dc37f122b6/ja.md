インプレースメソッド[`trilqr!`](@ref)のためのワークスペース。

このワークスペースを初期化するために使用できる外部コンストラクタは次のとおりです：

```
workspace = TrilqrWorkspace(m, n, S)
workspace = TrilqrWorkspace(A, b)
workspace = TrilqrWorkspace(kc::KrylovConstructor)
```
