```
struct ProductSemiring{T1<:Semiring, T2<:Semiring} <: Semiring{T}
    val1::T1
    val2::T2
end
```

Produc semiring $R = R_1 	imes R_2$ where $imes$ is the Cartesian product.
