```
euler_phi(x::ZZRingElem)
euler_phi(x::Int)
```

$ x $ のオイラー φ 関数の値を返します。すなわち、$ x $ と互いに素な $ x $ 以下の正の整数の数です。$ x \leq 0 $ の場合は例外が発生します。

# 例

```jldoctest
julia> euler_phi(ZZ(12480))
3072

julia> euler_phi(12480)
3072
```
