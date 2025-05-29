```
match_sequentially!(continuation_quantity::Vector{Dict}, rmaps::Vector{Dict})
```

上記の `match_sequentially!` と同様に、マッチングマップのベクターが与えられた場合、グローバル継続で追跡されている任意の量に対して実行します。`continuation_quantity` は例えば [`global_continuation`](@ref) の `fractions_cont` である可能性があります。
