```julia
zq = linterp1(x, y, z::AbstractMatrix, xq::Number, yq::Number; extrapolate=:Bilinear)
```

1次元の単純な線形補間。ノットのベクトル `x` と `y`、および値の行列 `z` が与えられたとき、位置 `xq`,`yq` での対応する `z` 値を見つけます。

ノットベクトル `x` と `y` は増加順にソートされている必要があり、次のように `z` の次元と一致しなければなりません：`eachindex(x) == axes(z,2)` および `eachindex(y) == axes(z,1)`

オプションのキーワード引数 `extrapolate` が `:Bilinear`（デフォルト）に設定されている場合、範囲外の `xq`,`yq` ペアは、最も近い4つの `z` 値に基づいて、`x` で線形に外挿（または補間）され、その後 `y` で線形に外挿されます（全体として二次的な結果を得る）。そうでない場合、`extrapolate` が `Number`（例：`0` または `NaN`）に設定されていると、その数値が代わりに使用されます。

### 例

```julia
julia> x = 1:3
 1:3

julia> y = 1:4
 1:4

julia> z = y*x'
4×3 Matrix{Int64}:
 1  2   3
 2  4   6
 3  6   9
 4  8  12

julia> linterp2(x,y,z,1.5,1.5)
 2.25

julia> linterp2(x,y,z,2.5,3.5)
 8.75

julia> linterp2(x,y,z,1,-10,extrapolate=:Bilinear)
 -10.0

julia> linterp2(x,y,z,2,-10,extrapolate=:Bilinear)
 -20.0
```
