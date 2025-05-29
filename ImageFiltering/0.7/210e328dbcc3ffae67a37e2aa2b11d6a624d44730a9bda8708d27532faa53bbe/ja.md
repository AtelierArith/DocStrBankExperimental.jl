```
blob_LoG(img, σscales; edges::Tuple=(true, false, ...), σshape::Tuple=(1, ...), rthresh=0.001) -> Vector{BlobLoG}
```

指定されたσ値のベクトルまたはタプルを使用して、N次元画像内の「ブロブ」を負のガウシアンラプラシアンを使用して見つけます。アルゴリズムは、フィルタリングされた画像（特定のσに対して）が、すべての空間的およびσ隣接ボクセルと比較してピークである場所を検索します。ここで、σは `σscales[i] * σshape` であり、iは任意の値です。デフォルトでは、`σshape` は1のntupleです。

オプションの `edges` 引数は、エッジ上のピークが含まれるかどうかを制御します。`edges` は `true` または `false` であるか、最初のエントリがエッジ-σ値がピークとして適格かどうかを制御し、残りのNエントリが `img` のN次元を制御するN+1タプルです。

`rthresh` は、-LoGフィルタリングされた画像内のピークの最小振幅を、`maximum(abs, img)` とガウシアンの体積の割合として制御します。

# 例

ほとんどの画像は2次元または3次元ですが、異なるサイズの2つのガウシアンブロブを含む1次元の「画像」でこれを示す方が簡単です：

```jldoctest; setup=:(using ImageFiltering), filter=r"amplitude=.*"
julia> σs = 2.0.^(1:6);

julia> img = zeros(100); img[20:30] = [exp(-x^2/(2*4^2)) for x=-5:5]; img[50:80] = [exp(-x^2/(2*8^2)) for x=-15:15];

julia> blob_LoG(img, σs; edges=false)
2-element Vector{BlobLoG{Float64, Tuple{Float64}, 1}}:
 BlobLoG(location=CartesianIndex(25,), σ=(4.0,), amplitude=0.10453155018303673)
 BlobLoG(location=CartesianIndex(65,), σ=(8.0,), amplitude=0.046175719034527364)
```

他の2つはそれぞれの「特徴」に中心を持ち、幅 `σ` は特徴自体の幅を反映しています。

`blob_LoG` は「ガウシアンのような」形状に対して最も効果的に機能しますが、ある程度一般化もします。

# 引用:

Lindeberg T (1998), "Feature Detection with Automatic Scale Selection", International Journal of Computer Vision, 30(2), 79–116.

参照: [`BlobLoG`](@ref).
