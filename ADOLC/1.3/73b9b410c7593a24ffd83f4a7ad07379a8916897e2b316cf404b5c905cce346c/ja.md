```
seed_idxs_adolc_format(partials::Vector{Vector{I}}) where I <: Integer
```

`partials`の実際に必要な導関数の方向を抽出し、昇順にソートして返します。

!!! note
    `partials`は[ADOLC-Format](@ref)である必要があります。


# 例

```jldoctest

partials = [[5, 5, 5, 1], [3, 1, 0, 0], [3, 3, 3, 0]]
seed_idxs_adolc_format(partials)

# 出力

3-element Vector{Int64}:
 1
 3
 5
```
