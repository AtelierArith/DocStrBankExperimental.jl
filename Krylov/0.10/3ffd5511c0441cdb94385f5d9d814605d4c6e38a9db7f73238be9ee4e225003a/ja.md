インプレースメソッド[`lsmr!`](@ref)のためのワークスペース。

このワークスペースを初期化するために使用できる外部コンストラクタは次のとおりです：

```
workspace = LsmrWorkspace(m, n, S)
workspace = LsmrWorkspace(A, b)
workspace = LsmrWorkspace(kc::KrylovConstructor)
```
