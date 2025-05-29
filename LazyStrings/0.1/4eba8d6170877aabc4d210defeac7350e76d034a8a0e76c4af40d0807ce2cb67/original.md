```
abstract type StringWrapper <: AbstractString end
```

Provides default `sw::StringWrapper<:AbstractString` API methods defering to `representation(sw)` call, by default `sw.x`.
