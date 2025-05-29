```
struct Polynomial{CoeffType,T<:AbstractTerm{CoeffType},V<:AbstractVector{T}} <: AbstractPolynomial{CoeffType}
    terms::V
end
```

非ゼロ項のベクトルとして、昇順の単項式順序でソートされた多変数多項式の表現。
