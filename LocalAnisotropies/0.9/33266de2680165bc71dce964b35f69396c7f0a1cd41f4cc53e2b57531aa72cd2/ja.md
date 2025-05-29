```
localanisotropies(data, rotation, ranges, convention=nothing)
localanisotropies(data, ranges, convention) # assumes angles [:ang1,:ang2,:ang3]
localanisotropies(data, ranges) # assumes quaternions [:q0,:q1,:q2,:q3]
```

`LocalAnisotropy`オブジェクトを表形式のデータからインポートします。`data`は`Tables.jl`構造に従う必要があります。回転情報と範囲がプロパティとして含まれている必要があります。これらのプロパティ名は、変換のために`rotation`と`ranges`のベクトルとして指定されます。利用可能な回転規則については、[`RotationRule`](@ref)のドキュメントを参照してください。

## 例

```julia
localanisotropies(data, [:rot1], [:range1, :range2], :EulerIntr) # 2D
localanisotropies(data, [:rot1, :rot2, :rot3], [:range1, :range2, :range3], :GSLIB) # 3D
localanisotropies(data, [:q0,:q1,:q2,:q3], [:range1, :range2, :range3]) # quaternion
```
