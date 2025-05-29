```
get_type(sym::Symbol) -> type (preferred)

get_type(str::String) -> type
```

`str`に対応するE4ST関連の`type`を返します。`reload_types!`も参照してください。

# 例:

```julia
julia> get_type("MyType")
ERROR: MyTypeという型は定義されていません!
julia> struct MyType <: Policy end
julia> T = get_type("MyType")
MyType
julia> T()
MyType()
```
