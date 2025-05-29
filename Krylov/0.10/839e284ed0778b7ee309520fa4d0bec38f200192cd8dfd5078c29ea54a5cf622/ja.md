インプレースメソッド[`bicgstab!`](@ref)のためのワークスペース。

このワークスペースを初期化するために使用できる外部コンストラクタは次のとおりです：

```
workspace = BicgstabWorkspace(m, n, S)
workspace = BicgstabWorkspace(A, b)
workspace = BicgstabWorkspace(kc::KrylovConstructor)
```
