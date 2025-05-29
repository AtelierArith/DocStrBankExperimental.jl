```
rewrite_match_maps(r::Rule{:SqPO},m; pres::Union{Nothing, Presentation}=nothing)
```

セスキプッシュアウトはDPOと非常に似ていますが、プッシュアウト補完の代わりに最終的なプルバック補完を使用します。

```
r.L  r.R
```

L <-⌞K -> R m ↓    ↓k   ↓ r   I <- • ->⌜O      i   o
