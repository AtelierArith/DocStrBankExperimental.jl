```
layer(v)
```

`v`内および任意の可変ラッパー内にラップされた計算を返します。

# 例

```jldoctest
julia> using NaiveNASflux, Flux

julia> layer(fluxvertex(Dense(2,3), inputvertex("in", 2)))
Dense(2 => 3)       # 9 パラメータ
```
