```
sample(treev::Array{T,1},
       f    ::Function,
       δt   ::Float64) where {T <: iT}
```

`f`によってアクセスされる補間されたパラメータのために、`δt`によって決定された時刻でサンプリングされた各ツリーの行を持つ配列を返します。
