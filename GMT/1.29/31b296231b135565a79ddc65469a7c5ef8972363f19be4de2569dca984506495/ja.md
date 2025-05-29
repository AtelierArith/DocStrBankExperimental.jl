```
quadkey(lon::Real, lat::Real, zoom::Int; bounds=false, geog=true)
```

  * `bounds`: true の場合、タイルのバウンディングボックスを返します。そうでない場合は、タイルの XYZ 座標とクワッドツリー文字列を返します。
  * `geog`: バウンディングボックスを地理座標で返します。false の場合、球面メルカトル座標でバウンディングボックスを返します。

x,y,z とクワッドツリー文字列またはバウンディングボックスを返します。

### 例

```jldoctest
julia> quadkey(-9,39, 8)
([121, 97, 8], ["03311003";;])
```

```jldoctest
julia> quadkey(-9,39, 8, bounds=true)
2×2 Matrix{Float64}:
 -9.84375  38.8226
 -8.4375   39.9097
```

以下の形式は、XYZ タイルのクワッドツリー表現または地理座標でのバウンディングボックス座標を返します。

```
quadkey(xyz::VecOrMat{<:Int}; bounds=true, geog=true)
```

### 例

```jldoctest
julia> quadkey([121, 97, 8], bounds=false)
"03311003"
```
