```
binomial2(x::Union{Int,StaticInt,Dynamic}) -> Union{Int,StaticInt,Dynamic}
```

`x`の2番目の二項係数を計算します。

この関数は`binomial(x, 2)`の便利なショートハンドです。

```julia-repl
julia> binomial2(4)
6
```
