```
ket_from_string(
    ket::String,
    levels::Vector{Int};
    level_dict=Dict(:g => 0, :e => 1, :f => 2, :h => 3, :i => 4, :j => 5, :k => 6, :l => 7),
    return_states=false
)
```

Construct a quantum state from a string ket representation.
