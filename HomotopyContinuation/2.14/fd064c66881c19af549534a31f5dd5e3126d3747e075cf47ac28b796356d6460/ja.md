```
singular(result; multiple_results=false, kwargs...)
```

解が単一であるすべての [`PathResult`] を返します。 `multiple_results=false` の場合、複数の解の各クラスターから1つの点のみが返されます。 `multiple_results = true` の場合、`R` 内のすべての単一解が返されます。可能な `kwargs` については [`results`](@ref) を参照してください。
