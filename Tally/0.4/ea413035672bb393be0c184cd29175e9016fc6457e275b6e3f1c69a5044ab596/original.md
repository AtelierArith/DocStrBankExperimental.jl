```
prison_count(T::Tally)
```

Print the tally using prison style:

```jldoctest
julia> T = tally([1, 1, 1, 2, 2, 2, 2, 2, 2, -1]);

julia> prison_count(T)
2  ┃ ┼┼┼┼ │
━━━╋━━━━━━━
1  ┃ │││
━━━╋━━━━━━━
-1 ┃ │
```
