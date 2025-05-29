```julia
@with_fields atypename fields...
```

抽象型 `atypename` を定義するマクロで、サブタイプに `fields` を自動的に追加します。サブタイプはマクロ `@atypename` を使用して宣言されます。

# 例:

```julia
julia>  @with_fields abs_type a::Int b
julia>  @abs_type struct mystruct
            c::Float64
        end

julia> fieldnames(mystruct)
(:c, :a, :b)

julia> fieldtypes(mystruct)
(Float64, Int64, Any)

julia> mystruct <: abs_type
true


julia> abstract type supertype end
julia> @with_fields abs_type <: supertype field_a field_b
julia> abs_type <: supertype
true
```
