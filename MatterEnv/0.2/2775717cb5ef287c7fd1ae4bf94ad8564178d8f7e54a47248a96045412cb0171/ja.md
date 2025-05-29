```
Lattice{T <: Real}
```

格子のデータ型。

# フィールド

  * `lattice::Array{T, 2}`: 格子のための3×3行列を格納します
  * `a:Array{T, 1}`: 軸aの基底を格納します
  * `b:Array{T, 1}`: 軸bの基底を格納します
  * `c:Array{T, 1}`: 軸cの基底を格納します
