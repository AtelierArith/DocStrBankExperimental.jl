```
project!(c::Sequence, A::LinearOperator{ParameterSpace,<:VectorSpace})
```

`A`を`space(c)`内の[`Sequence`](@ref)として表現します。結果は`c`に上書きされて保存されます。

参照: [`project`](@ref).
