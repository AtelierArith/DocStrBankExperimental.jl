```
abstract type StringWrapper <: AbstractString end
```

デフォルトの `sw::StringWrapper<:AbstractString` API メソッドは、デフォルトで `sw.x` を呼び出す `representation(sw)` に委譲します。
