```
reconstruct(a::ZZRingElem, m::ZZRingElem)
reconstruct(a::ZZRingElem, m::Integer)
reconstruct(a::Integer, m::ZZRingElem)
reconstruct(a::Integer, m::Integer)
```

有理数 $n/d$ を返すことを試みます。ここで、$0 \leq |n| \leq \lfloor\sqrt{m/2}\rfloor$ かつ $0 < d \leq \lfloor\sqrt{m/2}\rfloor$ であり、gcd$(n, d) = 1$ かつ $a \equiv nd^{-1} \pmod{m}$ となるようにします。解が存在しない場合は、例外がスローされます。

# 例

```jldoctest
julia> a = reconstruct(7, 13)
1//2

julia> b = reconstruct(ZZ(15), 31)
-1//2

julia> c = reconstruct(ZZ(123), ZZ(237))
9//2
```
