```
arecompatible(s::Split, t::Split[, mask::Array{Bool}])
```

スプリット `s` と `t` は **クラスタの観点から** 互換性があります。

```
arecompatible(s::SplitList, i::Integer, j::Integer; mask=true)
```

`s.splits[i]` と `s.splits[j]` は **クラスタの観点から** 互換性がありますか？
