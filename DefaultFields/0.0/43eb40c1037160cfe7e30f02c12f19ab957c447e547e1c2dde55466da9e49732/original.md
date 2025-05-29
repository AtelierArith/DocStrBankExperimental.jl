```julia
@with_fields atypename fields...
```

Macro to define an abstract type `atypename` that automatically adds `fields` to its subtypes. The subtypes are declared using the macro `@atypename`.

# Examples:

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
