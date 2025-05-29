```
MaxTree(image::GenericGrayImage; connectivity=1, rev=false) -> MaxTree
```

`image`の*max-tree*を構築します。

# 引数

  * `connectivity::Integer=1`: 接続されたコンポーネントを構築するために使用されるピクセルの近傍を定義します。この値は、隣接するピクセルに到達するための最大の直交ステップ数です。2Dでは、4近傍の場合は1、8近傍の場合は2です。[`rebuild!](@ref)）を参照してください。
  * `rev::Bool=false`: `false`の場合、max-treeは最も暗い（ルートノード）から最も明るい方向にトラバースされます。そうでない場合は、最も明るい（ルート）から最も暗い方向にトラバースされます。

# 例

小さなサンプル画像（[4]の図1）を作成し、max-treeを構築します。

```jldoctest; setup = :(using ImageMorphology), filter = r"Array{Int64,2}|Matrix{Int64}"
julia> image = [15 13 16; 12 12 10; 16 12 14]
3×3 Array{Int64,2}:
 15  13  16
 12  12  10
 16  12  14

julia> mtree = MaxTree(image, connectivity=2)
MaxTree{2}(false, [4 2 4; 8 2 8; 2 2 2], [8, 2, 5, 6, 4, 9, 1, 3, 7])
```
