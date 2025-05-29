```
Fun()
```

`Fun(identity, Chebyshev())`を返します。これは`-1..1`の範囲での恒等関数を表します。

# 例

```jldoctest
julia> f = Fun(Chebyshev())
Fun(Chebyshev(), [0.0, 1.0])

julia> f(0.1)
0.1
```
