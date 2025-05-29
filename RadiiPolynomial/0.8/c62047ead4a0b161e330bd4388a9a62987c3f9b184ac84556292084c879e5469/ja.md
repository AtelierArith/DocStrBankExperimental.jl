```
project!(C::LinearOperator, ℐ::Integral)
```

`ℐ`を`domain(C)`から`codomain(C)`への[`LinearOperator`](@ref)として表現します。結果は`C`に上書きされて保存されます。

関連情報: [`project(::Integral, ::VectorSpace, ::VectorSpace)`](@ref)および[`Integral`](@ref)
