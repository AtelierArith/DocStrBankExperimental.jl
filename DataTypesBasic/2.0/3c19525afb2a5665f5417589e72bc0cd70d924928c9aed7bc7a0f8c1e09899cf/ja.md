```
Option{T} = Union{Const{Nothing}, Identity{T}}
Option(nothing) == Const(nothing)
Option("anything but nothing") == Identity("anything but nothing")
Option() == Const(nothing)
```

`Union{T, Nothing}`のように、ただしコンテナのセマンティクスを持ちます。`Union{T, Nothing}`は存在するかしないかの値のように考えられますが、`Option{T} = Union{Identity{T}, Const{Nothing}}`は空であるか、正確に1つの要素を持つコンテナです。

単一要素コンテナを表すために[`Identity`](@ref)を再利用し、空のコンテナとして`Const(nothing)`を使用します。
