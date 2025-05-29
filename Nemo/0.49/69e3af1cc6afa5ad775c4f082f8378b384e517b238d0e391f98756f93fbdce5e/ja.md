```
mod(a::QQFieldElem, b::ZZRingElem)
mod(a::QQFieldElem, b::Integer)
```

整数 $b$ が $a$ の分母と互いに素である場合、$a \pmod{b}$ を返します。

# 例

```jldoctest
julia> mod(-ZZ(2)//3, 7)
4

julia> mod(ZZ(1)//2, ZZ(5))
3
```
