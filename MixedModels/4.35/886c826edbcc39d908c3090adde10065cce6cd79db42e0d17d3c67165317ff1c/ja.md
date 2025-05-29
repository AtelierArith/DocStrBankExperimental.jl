```
 profilevc(m::LinearMixedModel{T}, val::T, rowj::AbstractVector{T}) where {T}
```

分散成分の要素をプロファイルします。

!!! note
    このメソッドは `profile` によって呼び出され、現在は内部的なものと見なされています。そのため、将来のリリースで変更されたり、消失したりする可能性があり、破壊的な変更とは見なされません。

