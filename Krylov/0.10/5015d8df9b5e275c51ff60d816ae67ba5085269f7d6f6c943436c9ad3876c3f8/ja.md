インプレースメソッド[`cg_lanczos!`](@ref)のためのワークスペース。

このワークスペースを初期化するために使用できる外部コンストラクタは次のとおりです：

```
workspace = CgLanczosWorkspace(m, n, S)
workspace = CgLanczosWorkspace(A, b)
workspace = CgLanczosWorkspace(kc::KrylovConstructor)
```
