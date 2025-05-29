```
complete(t::Type)::Type{<:t}
```

`t`のより具体的なサブタイプを返します。

この関数にメソッドを追加しないでください。それが[`complete_overload`](@ref)の目的です。
