```
project!(C::LinearOperator, 𝒮::Shift)
```

`𝒮`を`domain(C)`から`codomain(C)`への[`LinearOperator`](@ref)として表現します。結果は`C`に上書きされて保存されます。

関連情報: [`project(::Shift, ::VectorSpace, ::VectorSpace)`](@ref)および[`Shift`](@ref)。
