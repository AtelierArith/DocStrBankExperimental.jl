```
exponent(x) -> Int
```

`2^y ≤ abs(x)` を満たす最大の整数 `y` を返します。正規化された浮動小数点数 `x` に対して、これは `x` の指数に対応します。

# 例

```jldoctest
julia> exponent(8)
3

julia> exponent(64//1)
6

julia> exponent(6.5)
2

julia> exponent(16.0)
4

julia> exponent(3.142e-4)
-12
```
