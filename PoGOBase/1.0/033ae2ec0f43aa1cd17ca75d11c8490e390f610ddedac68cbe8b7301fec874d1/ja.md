```
matching_pokemon(name::AbstractString, types::AbstractString; kwargs...) → species
```

与えられた名前とタイプに一致する `Species` オブジェクトのリストを返します。

# 例

```jldoctest
julia> matching_pokemon("rattata", "dark/normal")
1-element Vector{Species}:
 RATTATA_ALOLA (DARK/NORMAL): (103, 70, 102); Fast: ["TACKLE_FAST", "QUICK_ATTACK_FAST"]; Charged: ["CRUNCH", "HYPER_FANG", "SHADOW_BALL"]
```
