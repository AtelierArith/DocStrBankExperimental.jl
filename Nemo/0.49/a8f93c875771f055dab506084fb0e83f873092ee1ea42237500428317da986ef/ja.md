```
finite_field(p::IntegerUnion, d::Int, s::VarName = :o; cached::Bool = true, check::Bool = true)
finite_field(q::IntegerUnion, s::VarName = :o; cached::Bool = true, check::Bool = true)
finite_field(f::FqPolyRingElem, s::VarName = :o; cached::Bool = true, check::Bool = true)
```

有限体 $K$ のタプル $(K, x)$ を返します。ここで、$K$ は $q = p^d$ の順序を持ち、$p$ は素数であり、$x$ は $K$ の生成元です（定義については [`gen`](@ref) を参照してください）。識別子 $s$ は有限体生成元の印刷方法を指定するために使用されます。

有限体 $k$ 上の多項式 $f \in k[X]$ が指定されている場合、有限体 $K = k[X]/(f)$ は基底体 $k$ を持つ有限体として構築されます。

また、$K$ のみを返す [`GF`](@ref) も参照してください。

# 例

```jldoctest
julia> K, a = finite_field(3, 2, "a")
(Finite field of degree 2 and characteristic 3, a)

julia> K, a = finite_field(9, "a")
(Finite field of degree 2 and characteristic 3, a)

julia> Kx, x = K["x"];

julia> L, b = finite_field(x^3 + x^2 + x + 2, "b")
(Finite field of degree 3 over GF(3, 2), b)
```
