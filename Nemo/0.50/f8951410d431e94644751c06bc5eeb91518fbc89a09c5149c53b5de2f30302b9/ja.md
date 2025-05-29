```
GF(p::IntegerUnion, d::Int, s::VarName = :o; cached::Bool = true, check::Bool = true)
GF(q::IntegerUnion, s::VarName = :o; cached::Bool = true, check::Bool = true)
GF(f::FqPolyRingElem, s::VarName = :o; cached::Bool = true, check::Bool = true)
```

有限体 $K$ を順序 $q = p^d$ で返します。ここで、$p$ は素数です。識別子 $s$ は有限体生成器がどのように印刷されるかを指定するために使用されます。

有限体 $k$ 上の多項式 $f \in k[X]$ が指定されると、有限体 $K = k[X]/(f)$ が基底体 $k$ を持つ有限体として構築されます。

さらに、有限体生成器 $K$ を返す [`finite_field`](@ref) も参照してください。

# 例

```jldoctest
julia> K = GF(3, 2, "a")
有限体の次数 2 と特性 3

julia> K = GF(9, "a")
有限体の次数 2 と特性 3

julia> Kx, x = K["x"];

julia> L = GF(x^3 + x^2 + x + 2, "b")
GF(3, 2) 上の次数 3 の有限体
```
