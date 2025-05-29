```julia
fixed_transform(mechanism, from, to)

```

`CartesianFrame3D` `from` から `to` への変換を返します。どちらも同じ `RigidBody` に剛体的に取り付けられています。

注意: この関数はボディの数に対して線形であり、タイトなループ内で呼び出すことを意図していません。
