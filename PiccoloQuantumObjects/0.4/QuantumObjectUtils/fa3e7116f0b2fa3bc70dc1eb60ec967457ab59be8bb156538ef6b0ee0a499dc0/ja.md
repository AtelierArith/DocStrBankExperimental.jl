```
ket_from_string(
    ket::String,
    levels::Vector{Int};
    level_dict=Dict(:g => 0, :e => 1, :f => 2, :h => 3, :i => 4, :j => 5, :k => 6, :l => 7),
    return_states=false
)
```

文字列のケト表現から量子状態を構築します。
