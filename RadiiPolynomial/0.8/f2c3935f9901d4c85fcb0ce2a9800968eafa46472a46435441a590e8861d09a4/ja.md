```
project!(C::LinearOperator, Δ::Laplacian)
```

`Δ`を`domain(C)`から`codomain(C)`への[`LinearOperator`](@ref)として表現します。結果は`C`に上書きされて保存されます。

関連情報: [`project(::Laplacian, ::VectorSpace, ::VectorSpace)`](@ref)および[`Laplacian`](@ref)
