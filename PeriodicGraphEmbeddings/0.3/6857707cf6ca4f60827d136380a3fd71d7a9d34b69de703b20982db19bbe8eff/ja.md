```
find_symmetries(pge::PeriodicGraphEmbedding3D, vtypes=nothing, check_symmetry=check_valid_symmetry; tolerance::Union{Nothing,Cdouble}=nothing)
```

[`SymmetryGroup3D`](@ref) オブジェクトを返し、spglibを使用して見つけたグラフ埋め込みの対称操作のリストを格納します。グラフ埋め込みの[`Cell`](@ref)に既に指定されている対称性を単純に抽出するには、[`retrieve_symmetries`](@ref)を使用します。

`vtypes !== nothing`の場合、`vtypes[x] != vtypes[y]`である場合、2つの頂点`x`と`y`は対称関係にないことを確認します。

`check_symmetry`は、`check_valid_symmetry`と同じ4つの引数`pge`、`t`、`r`、および`vtypes`を受け取り、入力が有効な対称性でない場合は`(vmap, offsets)`または`nothing`を返す関数でなければなりません。これは、`vtypes`だけでは運ぶことができない追加の制約を指定するために使用できます。

明示的な許容誤差を設定できます。そうでない場合、位置が浮動小数点の場合は緩い許容誤差、または有理数の場合は厳格な許容誤差がデフォルトとなります。
