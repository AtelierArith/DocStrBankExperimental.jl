インプレースメソッド[`cg!`](@ref)のためのワークスペース。

このワークスペースを初期化するために使用できる外部コンストラクタは次のとおりです：

```
workspace = CgWorkspace(m, n, S)
workspace = CgWorkspace(A, b)
workspace = CgWorkspace(kc::KrylovConstructor)
```
