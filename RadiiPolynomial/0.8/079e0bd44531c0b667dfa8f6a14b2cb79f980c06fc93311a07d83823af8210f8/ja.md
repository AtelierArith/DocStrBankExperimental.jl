```
project!(C::LinearOperator{<:SequenceSpace,<:SequenceSpace}, ℳ::Multiplication)
```

`ℳ`を`domain(C)`から`codomain(C)`への[`LinearOperator`](@ref)として表現します。結果は`C`に上書きされて保存されます。

関連情報: [`project(::Multiplication, ::SequenceSpace, ::SequenceSpace)`](@ref)および[`Multiplication`](@ref)。
