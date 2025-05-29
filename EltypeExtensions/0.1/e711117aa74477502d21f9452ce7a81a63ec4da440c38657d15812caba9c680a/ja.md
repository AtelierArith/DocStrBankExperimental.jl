```
precisiontype(T::Type)
```

`T`の精度を決定する型を返します。[`basetype`](@ref)との違いは、`precisiontype`が`Complex`のような複合ベース型をアンラップすることであり、`precisiontype`は一般化されていないことです。

# 例

```jldoctest; setup = :(using EltypeExtensions: precisiontype)
julia> precisiontype(Complex{Float32})
Float32

julia> precisiontype(Matrix{ComplexF64})
Float64
```
