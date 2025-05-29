```
windowmap(f::Function, x::AbstractVector; kwargs...) → mapped_f
```

最初に `wv = WindowViewer(x; kwargs...)` を生成し、その後 `mapped_f = map(f, wv)` を適用するためのショートカットです。もし `x` に時間ベクトル `t` が伴う場合、`f` に `mean, midpoint, midvalue` のいずれかを指定して `t` でこの関数を呼び出すことで、`mapped_f` 出力のための時間ベクトルを取得することをお勧めします。
