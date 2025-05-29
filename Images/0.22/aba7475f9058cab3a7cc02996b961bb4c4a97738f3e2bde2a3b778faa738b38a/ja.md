```
blob_LoG(img, σscales, [edges], [σshape]) -> Vector{BlobLoG}
```

指定されたσ値のベクトルまたはタプルを使用して、N次元画像内の「ブロブ」を負のガウスのラプラシアンで見つけます。アルゴリズムは、フィルタリングされた画像（特定のσに対して）が、すべての空間的およびσ隣接ボクセルと比較してピークである場所を検索します。ここで、σは `σscales[i] * σshape` であり、iは任意の値です。デフォルトでは、`σshape` は1のntupleです。

オプションの `edges` 引数は、エッジ上のピークが含まれるかどうかを制御します。`edges` は `true` または `false` であるか、最初のエントリがエッジ-σ値がピークとして適格かどうかを制御し、残りのNエントリが `img` のN次元それぞれを制御するN+1タプルです。

# 引用:

Lindeberg T (1998), "Feature Detection with Automatic Scale Selection", International Journal of Computer Vision, 30(2), 79–116.

参照: [`BlobLoG`](@ref).
