```
mlaplacian(img; dims=coords_spatial(img), r=1)
mlaplacian(img, se)
```

画像の形態学的ラプラシアンを計算します。

形態学的ラプラシアン演算子は `∇⁺A - ∇⁻A` と定義され、ここで `∇⁺A` は外部勾配 `A - erode(A, se)` であり、`∇⁻A` は内部勾配 `dilate(A, se) - A` です。したがって、これは `dilate(A, se) + erode(A, se) - 2A` となります。

`se` は画像の近傍を定義する構造要素です。詳細については [`strel`](@ref) を参照してください。`se` が指定されていない場合、次のキーワード `dims` を使用してフィルタリングする次元を制御する [`strel_box`](@ref) が使用されます。

# 例

```jldoctest; setup = :(using ImageMorphology)
julia> img = falses(7, 7); img[3:5, 3:5] .= true; img[4, 4] = false; img
7×7 BitMatrix:
 0  0  0  0  0  0  0
 0  0  0  0  0  0  0
 0  0  1  1  1  0  0
 0  0  1  0  1  0  0
 0  0  1  1  1  0  0
 0  0  0  0  0  0  0
 0  0  0  0  0  0  0

julia> Int.(mlaplacian(img))
7×7 Matrix{Int64}:
 0  0   0   0   0  0  0
 0  1   1   1   1  1  0
 0  1  -1  -1  -1  1  0
 0  1  -1   1  -1  1  0
 0  1  -1  -1  -1  1  0
 0  1   1   1   1  1  0
 0  0   0   0   0  0  0

julia> Int.(mlaplacian(img, strel_diamond(img))) # ダイヤモンド形状のSEを使用
7×7 Matrix{Int64}:
 0  0   0   0   0  0  0
 0  0   1   1   1  0  0
 0  1  -1  -1  -1  1  0
 0  1  -1   1  -1  1  0
 0  1  -1  -1  -1  1  0
 0  0   1   1   1  0  0
 0  0   0   0   0  0  0
```

## 参照

  * [`mlaplacian!`](@ref) はこの関数のインプレースバージョンです。
  * [`mgradient`](@ref) は勾配演算子です。
  * `ImageBase.FiniteDiff` は `fdiff`、`fgradient` などのいくつかの有限差分演算子も提供します。
