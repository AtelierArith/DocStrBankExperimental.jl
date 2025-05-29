```
generators(num::Integer, T::Type{AbstractGroup{D}}[, optargs])
generators(pgiuc::String, T::PointGroup{D}})              -->  Vector{SymOperation{D}}
```

群のタイプ `T` の生成子を返します。`T` は `SpaceGroup{D}` または `PointGroup{D}` であり、次元性 `D` によってパラメータ化されています。`T` に応じて、群は最初の引数として入力することによって決定されます：

  * `SpaceGroup{D}`: 空間群番号 `num::Integer`。
  * `PointGroup{D}`: 点群 IUC ラベル `pgiuc::String`（[`pointgroup(::String)`](@ref) も参照）または標準点群番号 `num::Integer`、これはオプションで整数値の設定選択 `setting::Integer` で補足することができます（[`pointgroup(::Integer, ::Integer, ::Integer)`](@ref) も参照）。
  * `SubperiodicGroup{D}`: 副周期群番号 `num::Integer`。

設定選択は [`spacegroup`](@ref)、[`pointgroup`](@ref)、および [`subperiodicgroup`](@ref) のものと一致します。

返された対称操作の反復合成は、関連する空間群または点群のすべての操作を生成します（[`generate`](@ref) を参照）。例えば、`generate(generators(num,`SpaceGroup{D}))`と`spacegroup(num, D)` は同一の操作を返します（通常は異なるソートで）；点群および副周期群についても同様です。

## 例

空間群 200 の生成子：

```jldoctest
julia> generators(200, SpaceGroup{3})
4-element Vector{SymOperation{3}}:
 2₀₀₁
 2₀₁₀
 3₁₁₁⁺
 -1
```

点群 m-3m の生成子：

```jldoctest
julia> generators("2/m", PointGroup{3})
2-element Vector{SymOperation{3}}:
 2₀₁₀
 -1
```

フリーズ群 𝓅2mg の生成子：

```jldoctest
julia> generators(7, SubperiodicGroup{2, 1})
2-element Vector{SymOperation{2}}:
 2
 {m₁₀|½,0}
```

## 引用

公開された作品で使用する場合は、元のデータソースを引用してください：

  * 空間群: [Aroyo et al., Z. Kristallogr. Cryst. Mater. **221**, 15 (2006)](https://doi.org/10.1524/zkri.2006.221.1.15);
  * 点群: ビルバオ結晶学サーバーの [2D および 3D GENPOS](https://www.cryst.ehu.es/cryst/get_point_genpos.html);
  * 副周期群: ビルバオ結晶学サーバーの [SUBPERIODIC GENPOS](https://www.cryst.ehu.es/subperiodic/get_sub_gen.html)。

## 拡張ヘルプ

返された生成子が最小の生成子の集合であることは保証されていません。つまり、要素数が少ない他の生成子が存在する可能性があります（例として、空間群 168 (P6) では、返された生成子は `[2₀₀₁, 3₀₀₁⁺]` ですが、群は `[6₀₀₁⁺]` のみで生成できます）。さらに、返された生成子は [最小](https://en.wikipedia.org/wiki/Generating_set_of_a_module) であることも保証されていません。つまり、群自体を生成する適切な部分集合を含む可能性があります（例として、空間群 75 (P4) では、返された生成子は `[2₀₀₁, 4₀₀₁⁺]` ですが、部分集合 `[4₀₀₁⁺]` だけで群を生成するのに十分です）。これは、類似の結晶系に対してできるだけ類似の生成子を提示することを目的としています（さらなる背景については、国際結晶学表 Vol. A, Ed. 5 (ITA) のセクション 8.3.5 を参照してください）。

また、ITA の慣習とは異なり、恒等操作は返された生成子の中に含まれていません（空間群 1 を除く）。これは、恒等操作が自明に合成され、追加の文脈を提供しないためです。
