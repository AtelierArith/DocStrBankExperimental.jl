インプレースメソッド[`cgs!`](@ref)のためのワークスペース。

このワークスペースを初期化するために使用できる外部コンストラクタは次のとおりです:

```
workspace = CgsWorkspace(m, n, S)
workspace = CgsWorkspace(A, b)
workspace = CgsWorkspace(kc::KrylovConstructor)
```
