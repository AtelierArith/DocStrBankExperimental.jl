```
masked(x, [j::Integer], i::Integer) -> typeof(x)
```

マスク `mask(x, [j], i)` を `x` に適用した結果を返します。すなわち、`x & mask(x, [j], i)` です。もし `x` が浮動小数点数であれば、マスクを基になるビットに適用します。

# 例

```jldoctest
julia> masked(0b11110011, 1, 5) === 0b00010010
true

julia> x = rand(); masked(-x, 0, 63) === x
true
```
