```
project!(C::LinearOperator{ParameterSpace,<:VectorSpace}, a::Sequence)
```

`a`を`ParameterSpace`から`codomain(C)`への[`LinearOperator`](@ref)として表現します。結果は`C`に上書きされて保存されます。

関連情報: [`project`](@ref).
