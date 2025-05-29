```
DistanceMap(element)
DistanceMap(element_one, element_two)
DistanceMap(float_array_2D)
```

`StructuralElementOrList`の距離マップを計算するか、2つの`StructuralElementOrList`間の距離を計算します。

これは、サブ要素間の最小距離を持つ`Array{Float64, 2}`を含む`DistanceMap`型を返します。1つの要素が入力として与えられた場合、これは対称の正方行列を返します。`DistanceMap` `dm`の基礎データに直接アクセスするには、`dm.data`を使用します。

# 例

```julia
cbetas_A = collectatoms(struc["A"], cbetaselector)
cbetas_B = collectatoms(struc["B"], cbetaselector)

# チェーンAのCβ原子が他の原子からどれだけ離れているかを示す距離マップ
dm = DistanceMap(cbetas_A)

# 10番目と20番目の要素間の距離を返す
dm[10, 20]

# チェーンAとBの長方形距離マップ
dm = DistanceMap(cbetas_A, cbetas_B)

# 距離マップをファイルに書き込む
using DelimitedFiles
writedlm("distances.out", dm.data, " ")
```
