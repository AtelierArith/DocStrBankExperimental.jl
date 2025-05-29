```
ContactMap(element, contact_distance)
ContactMap(element_one, element_two, contact_distance)
ContactMap(bit_array_2D)
```

`StructuralElementOrList`の接触マップを計算するか、2つの`StructuralElementOrList`間の接触マップを計算します。

これは、サブ要素が接触距離以内にある場合に`true`、そうでない場合に`false`を持つ`BitArray{2}`を含む`ContactMap`型を返します。1つの要素が入力として与えられた場合、これは対称の正方行列を返します。`ContactMap` `cm`の基礎データに直接アクセスするには、`cm.data`を使用します。

# 例

```julia
cbetas_A = collectatoms(struc["A"], cbetaselector)
cbetas_B = collectatoms(struc["B"], cbetaselector)

# 従来のCβおよび8Åの定義を使用した鎖Aの接触マップ
cm = ContactMap(cbetas_A, 8.0)

# 10番目と20番目の要素の間に接触が存在する場合はtrueを返す
cm[10, 20]

# 鎖AとBの長方形接触マップ
cm = ContactMap(cbetas_A, cbetas_B, 8.0)

# 接触マップをファイルに書き込む
using DelimitedFiles
writedlm("contacts.out", Int64.(cm.data), " ")
```
