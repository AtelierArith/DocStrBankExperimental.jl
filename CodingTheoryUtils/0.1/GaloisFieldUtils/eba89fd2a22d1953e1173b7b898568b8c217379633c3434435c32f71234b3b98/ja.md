```
one_hot_vector(len::Int, pos::Int, v::F) where F <: AbstractGaloisField -> Vector{F}
```

長さ `len` のワンホットベクトルを作成し、位置 `pos` に値 `v` を配置します。他のすべての要素はフィールド `F` でゼロになります。

# 引数

  * `len::Int`: 結果のベクトルの長さ。
  * `pos::Int`: 値 `v` を配置する1ベースのインデックス。
  * `v::F`: 指定された位置に配置する値。

# 戻り値

  * `Vector{F}`: 結果のワンホットベクトル。

# 例

julia> one*hot*vector(5, 3, F2(1)) 5-element Vector{F2}:  0  0  1  0  0

julia> GF8, α = GaloisField(2, 3, :α);

julia> one*hot*vector(4, 2, α^3) 4-element Vector{GF8}:  0  α^3  0  0
