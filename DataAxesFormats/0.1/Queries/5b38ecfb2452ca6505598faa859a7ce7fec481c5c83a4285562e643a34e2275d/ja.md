```
IsMatch(value::Union{AbstractString, Regex}) <: QueryOperation
```

[`IsLess`](@ref)と似ていますが、比較される値は文字列でなければならず、マスクは指定された正規表現に一致する値です。
