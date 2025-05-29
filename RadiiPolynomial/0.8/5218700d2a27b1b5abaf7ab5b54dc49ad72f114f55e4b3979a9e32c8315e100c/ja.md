```
project!(C::LinearOperator, ℰ::Evaluation)
```

`ℰ`を`domain`から`codomain`への[`LinearOperator`](@ref)として表現します。結果は`C`に上書きされて保存されます。

関連情報: [`project(::Evaluation, ::VectorSpace, ::VectorSpace)`](@ref)および[`Evaluation`](@ref)。
