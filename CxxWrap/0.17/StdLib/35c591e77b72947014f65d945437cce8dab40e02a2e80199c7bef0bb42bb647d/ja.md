```
StdString(str::Union{Cstring, Base.CodeUnits, Vector{UInt8}, Ref{Int8}, Array{Int8}})
```

ヌル終端文字列から `StdString` を作成します。

ヌル文字 ('\0') を含む `StdString` を構築したい場合は、[`StdString(::String)`](@ref) または [`StdString(::Any, ::Int)`](@ref) を使用してください。

## 例

```julia
julia> StdString(b"visible\0hidden")
"visible"
```
