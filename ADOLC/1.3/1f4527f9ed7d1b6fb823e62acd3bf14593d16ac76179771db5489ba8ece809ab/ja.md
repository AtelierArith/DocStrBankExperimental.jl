```
adolc_format_to_seed_space(partials::Vector{Vector{I_1}}, seed_idxs::Vector{I_2}) where {I_1 <: Integer, I_2 <: Integer}
adolc_format_to_seed_space(partials::Vector{Vector{I}}) where I <: Integer
```

[`partial_format_to_seed_space`](@ref) と同様ですが、[ADOLC-Format](@ref) を使用しています。

# 例

```jldoctest

partials = [[3, 2], [2, 2]]
seed_idxs = seed_idxs_adolc_format(partials)
adolc_format_to_seed_space(partials, seed_idxs)

# 出力

2-element Vector{Vector{Int64}}:
 [2, 1]
 [1, 1]
```

`seed_idxs`なし

```jldoctest

partials = [[3, 2], [2, 2]]
seed_idxs = seed_idxs_adolc_format(partials)
adolc_format_to_seed_space(partials, seed_idxs)

# 出力

2-element Vector{Vector{Int64}}:
 [2, 1]
 [1, 1]
```
