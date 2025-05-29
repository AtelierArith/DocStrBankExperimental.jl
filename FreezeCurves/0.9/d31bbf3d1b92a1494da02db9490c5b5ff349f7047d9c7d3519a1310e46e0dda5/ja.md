```
build_lut(f, coords::Pair{Symbol,<:Union{Number,AbstractVector}}...; f_kwargs...)
```

指定された `coords` に対して `f` を呼び出すことで n 次元のルックアップテーブル `LUT` を構築します。`f` は `coords` に一致するキーワード引数と、任意の追加の定数キーワード引数 `f_kwargs` を受け入れる関数である必要があります。

例:

```julia
f(; x=1.0, y=1.0) = x + y
lut = build_lut(f, :x => -10.0:10.0, :y=-10.0:10.0)
lut(; x=2.2, y=1.5)
# output
3.7
```
