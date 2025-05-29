```
integ!(t::TPS{T}, t1::TPS{T}, var=1) where {T} -> t
∫!(t::TPS{T}, t1::TPS{T}, var=1) where {T} -> t
```

変数 `var` に関して `t1` を積分し、結果を `t` に等しく設定します。
