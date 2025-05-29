```
project!(C::LinearOperator, 𝒮::Scale)
```

`𝒮`を`domain(C)`から`codomain(C)`への[`LinearOperator`](@ref)として表現します。結果は`C`に上書きされて保存されます。

関連情報: [`project(::Scale, ::VectorSpace, ::VectorSpace)`](@ref)および[`Scale`](@ref)
