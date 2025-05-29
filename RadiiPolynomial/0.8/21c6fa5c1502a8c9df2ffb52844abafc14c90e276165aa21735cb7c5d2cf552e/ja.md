```
project!(C::LinearOperator, J::UniformScaling)
```

`J`を`domain(C)`から`codomain(C)`への[`LinearOperator`](@ref)として表現します。結果は`C`に上書きされて保存されます。

参照: [`project`](@ref).
