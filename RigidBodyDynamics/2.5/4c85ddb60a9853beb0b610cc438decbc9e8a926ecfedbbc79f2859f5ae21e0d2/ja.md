```julia
principal_value!(state)

```

[Rotations.jl](https://github.com/FugroRoames/Rotations.jl/blob/d080990517f89b56c37962ad53a7fd24bd94b9f7/src/principal*value.jl)からのprincipal*value関数を関節角に適用します。これは現在、`SPQuatFloating`関節にのみ適用されます。

例えば：

  * 回転関節に対応する$q$の部分について、このメソッドは何もしません；
  * `SPQuatFloating`関節に対応する$q$の部分について、この関数は

`principal_value`を方向に適用します。
