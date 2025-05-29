```
prison_count(T::Tally)
```

囚人スタイルで集計を表示します：

```jldoctest
julia> T = tally([1, 1, 1, 2, 2, 2, 2, 2, 2, -1]);

julia> prison_count(T)
2  ┃ ┼┼┼┼ │
━━━╋━━━━━━━
1  ┃ │││
━━━╋━━━━━━━
-1 ┃ │
```
