```
windowmap(f::Function, x::AbstractVector; kwargs...) → mapped_f
```

最初に `wv = WindowViewer(x; kwargs...)` を生成し、その後 `mapped_f = map(f, wv)` を適用するためのショートカットです。もし `x` に時間ベクトル `t` が伴う場合、`x` の代わりに `t` を使い、`f` として `mean, midpoint, midvalue` のいずれかを指定して、この関数を呼び出すことをお勧めします。そうすることで、`mapped_f` 出力のための時間ベクトルを取得できます。
