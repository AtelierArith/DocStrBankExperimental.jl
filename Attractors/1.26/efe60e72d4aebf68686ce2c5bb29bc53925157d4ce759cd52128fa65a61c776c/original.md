```
match_sequentially!(continuation_quantity::Vector{Dict}, rmaps::Vector{Dict})
```

Do the same as in `match_sequentially!` above, now given the vector of matching maps, and for any arbitrary quantity that has been tracked in the global continuation. `continuation_quantity` can for example be `fractions_cont` from [`global_continuation`](@ref).
