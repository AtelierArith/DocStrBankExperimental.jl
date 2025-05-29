```
partial_format_to_seed_space(partials::Vector{Vector{I_1}}, seed_idxs::Vector{I_2}) where {I_1 <: Integer, I_2 <: Integer}
partial_format_to_seed_space(partials::Vector{Vector{I}}) where I <: Integer
```

`partials`を[Partial-Format](@ref)から同じ形式の`partials`に変換しますが、（可能な）導関数の方向数が減少します。`seed_idxs`は[`seed_idxs_partial_format(seed_idxs)`](@ref)の結果を格納することが期待されます。`seed_idxs`がない場合、関数は最初に[`seed_idxs_partial_format(seed_idxs)`](@ref)を呼び出してインデックスを取得します。

# 例

```jldoctest

partials = [[0, 1, 1], [0, 2, 0]]
seed_idxs = seed_idxs_partial_format(partials)
partial_format_to_seed_space(partials, seed_idxs)

# 出力

2-element Vector{Vector{Int64}}:
 [1, 1]
 [2, 0]
```

`seed_idxs`なし

```jldoctest

partials = [[0, 1, 1], [0, 2, 0]]
partial_format_to_seed_space(partials)

# 出力

2-element Vector{Vector{Int64}}:
 [1, 1]
 [2, 0]
```
