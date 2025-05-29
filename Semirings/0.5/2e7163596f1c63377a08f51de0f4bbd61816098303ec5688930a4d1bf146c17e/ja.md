```
struct ProductSemiring{T1<:Semiring, T2<:Semiring} <: Semiring{T}
    val1::T1
    val2::T2
end
```

プロダクト半環 $R = R_1 \times R_2$ ただし、$\times$ は直積です。
