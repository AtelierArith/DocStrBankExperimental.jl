```
cube_information(cube::String)
```

キューブの座標情報を計算します。

この関数は、キューブの座標情報を持つ整数ベクトルを返します。返されるベクトル `intinfo` のコンポーネントには、以下のデータが含まれています：

  * `1:pointdim`: アンカーポイントの座標
  * `1+pointdim:2*pointdim`: 各次元の区間の長さ
  * `1+2*pointdim`: キューブの次元

`pointdim` は、キューブを指定するポイントの次元に等しいことに注意してください。

# 例

```jldoctest
julia> cube_information("011654003.011")
7-element Vector{Int64}:
  11
 654
   3
   0
   1
   1
   2
```
