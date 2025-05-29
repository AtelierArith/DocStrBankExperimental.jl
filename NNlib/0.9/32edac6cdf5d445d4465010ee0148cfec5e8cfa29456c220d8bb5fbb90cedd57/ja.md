```
sigmoid_fast(x)
```

これは、`sigmoid`のより速く、わずかに精度が低いバージョンです。`x::Float32`の場合、約3倍速く、最大誤差は1ではなく2 epsです。

関連情報として[`tanh_fast`](@ref)も参照してください。

```julia-repl
julia> sigmoid(0.2f0)
0.54983395f0

julia> sigmoid_fast(0.2f0)
0.54983395f0

julia> hardσ(0.2f0)
0.53333336f0
```
