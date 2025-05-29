```
VarName{sym}(optic=identity)
```

シンボル `sym` とオプティック `optic` のための変数識別子。

モデル内の `sym` に対応するJulia変数は、単一の値または単変量、多変量、または行列変数の階層的配列構造を参照することができます。フィールド `lens` は、`sym` によって示されるJulia変数からランダム変数にアクセスするために必要なインデックスをタプルのタプルとして格納します。タプルの各要素は、1つのオプティック操作のインデックスを含みます。

`VarName` は、`VarName{sym}(optic)` コンストラクタを使用して手動で構築することも、オプティック式から [`@varname`](@ref) 便利マクロを通じて構築することもできます。

# 例

```jldoctest; setup=:(using Accessors)
julia> vn = VarName{:x}(Accessors.IndexLens((Colon(), 1)) ⨟ Accessors.IndexLens((2, )))
x[:, 1][2]

julia> getoptic(vn)
(@o _[Colon(), 1][2])

julia> @varname x[:, 1][1+1]
x[:, 1][2]
```
