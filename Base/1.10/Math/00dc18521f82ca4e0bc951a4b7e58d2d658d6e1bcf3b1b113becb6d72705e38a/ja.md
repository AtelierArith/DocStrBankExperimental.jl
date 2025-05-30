```
frexp(val)
```

返す `(x,exp)` は、`x` が区間 $[1/2, 1)$ または 0 の大きさを持ち、`val` が `x \times 2^{exp}` に等しいことを示します。

# 例

```jldoctest
julia> frexp(12.8)
(0.8, 4)
```
