```julia
indicator_group(F::Crystalline.SmithNormalForm.Smith) -> Any

```

入力されたバンド表現の集合 `brs`（またはそのスミス分解 `F`）に関連する対称指標群 $X^{\text{BS}}$ を返します。つまり、バンド表現行列のスミス正規形の非自明な（すなわち、≠ {0,1}）基本因子を返します。返り値は非自明な因子を含む `Vector{Int}` です。非自明な因子が存在しない場合、返り値は空の `Vector{Int}` になります。

フォーマットされた文字列バージョンについては、[`indicator_group_as_string`](@ref) を参照してください。

## 理解

対称指標群は、「$\mathbb{Z}_n$ 群の直積は、商群 $X^{\text{BS}} = \{\text{BS}\}/\{\text{AI}\}$ に同型であるか？」という質問に答えます（詳細については、[Po, Watanabe, & Vishwanath, Nature Commun. **8**, 50 (2017)](https://doi.org/10.1038/s41467-017-00133-2) を参照してください）。

## 例

```jldoctest
julia> brs = calc_bandreps(2, Val(3));

julia> indicator_group(brs)
4-element Vector{Int64}:
 2
 2
 2
 4
```
