```
impute!(data::T, imp; kwargs...) -> T where T <: AbstractVector{<:NamedTuple}
```

特別なケースの行テーブルは配列ですが、テーブルメソッドにフォールバックしたいです。
