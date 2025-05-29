```
validate(validator::Validator{T}, obj::T; contextkw...) -> Bool
```

与えられた `obj` が `validator` に対して有効な値であるかどうかをチェックします。

`Bool` を返すか、[`ValidationError`](@ref) をスローする必要があります。
