```
from_dict(::Type{T}, d::AbstractDict{String}; kw...) where T
```

Convert dictionary `d` to an option type `T`, the value of valid fields of `T` in this dictionary `d` can be override by keyword arguments.

!!! compat "Configurations 0.17"
    `convert_to_option` interface is deprecated for conversion, please overload the 3-arg or 4-arg `from_dict` instead. See also [Type Conversion](@ref type-conversion) section.


# Example

```julia-repl
julia> @option struct OptionA
           name::String = "Sam"
           age::Int = 25
       end

julia> d = Dict{String, Any}(
           "name" => "Roger",
           "age" => 10,
       );

julia> from_dict(OptionA, d; age=25)
OptionA(;
    name = "Roger",
    age = 25,
)
```
