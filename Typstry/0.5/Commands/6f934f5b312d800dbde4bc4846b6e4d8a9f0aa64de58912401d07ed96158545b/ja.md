```
TypstError <: Exception
TypstError(::TypstCommand)
```

`Exception`は、[`run`](@ref)を[`TypstCommand`](@ref)実行する際の失敗を示します。

# 例

```jldoctest
julia> TypstError(typst``)
TypstError(typst``)
```
