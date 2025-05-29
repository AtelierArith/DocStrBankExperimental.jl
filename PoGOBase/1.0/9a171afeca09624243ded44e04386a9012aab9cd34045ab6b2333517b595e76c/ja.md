```
matching_pokemon(name::AbstractString; tol=0.0, complete=false) → species
```

与えられた名前に一致する `Species` オブジェクトのリストを返します。`complete` が `true` の場合、名前は正確に一致する必要があります。

`tol` は、名前と種の名前との間のレーベンシュタイン距離の許容範囲を表します。

# 例

```jldoctest
julia> matching_pokemon("rattata")
2-element Vector{Species}:
 RATTATA (NORMAL): (103, 70, 102); Fast: ["TACKLE_FAST", "QUICK_ATTACK_FAST"]; Charged: ["DIG", "HYPER_FANG", "BODY_SLAM"]
 RATTATA_ALOLA (DARK/NORMAL): (103, 70, 102); Fast: ["TACKLE_FAST", "QUICK_ATTACK_FAST"]; Charged: ["CRUNCH", "HYPER_FANG", "SHADOW_BALL"]

julia> matching_pokemon("rattata"; complete=true)
1-element Vector{Species}:
 RATTATA (NORMAL): (103, 70, 102); Fast: ["TACKLE_FAST", "QUICK_ATTACK_FAST"]; Charged: ["DIG", "HYPER_FANG", "BODY_SLAM"]

julia> matching_pokemon("rattatta")      # スペルミス
Species[]

julia> matching_pokemon("rattatta"; tol=0.25)
2-element Vector{Species}:
 RATTATA (NORMAL): (103, 70, 102); Fast: ["TACKLE_FAST", "QUICK_ATTACK_FAST"]; Charged: ["DIG", "HYPER_FANG", "BODY_SLAM"]
 RATTATA_ALOLA (DARK/NORMAL): (103, 70, 102); Fast: ["TACKLE_FAST", "QUICK_ATTACK_FAST"]; Charged: ["CRUNCH", "HYPER_FANG", "SHADOW_BALL"]
```
