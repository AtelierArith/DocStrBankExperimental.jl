```
renamefields!(wrappers::Wrappers, type::Type, rename::Dict{Symbol,String})
renamefields!(wrappers::Wrappers, type::Type, rename::Vector{Pair{Symbol,String})
```

Change some field names of a struct. This can be useful if the name of a struct results in invalid Rust code or causes warnings.

# Example

```jldoctest
julia> using JlrsReflect

julia> struct Food burger::Bool end

julia> wrappers = reflect([Food]);

julia> renamefields!(wrappers, Food, [:burger => "hamburger"])

julia> wrappers
#[repr(C)]
#[derive(Clone, Debug, Unbox, ValidLayout, ValidField, Typecheck, IntoJulia)]
#[jlrs(julia_type = "Main.Food")]
pub struct Food {
    pub hamburger: ::jlrs::wrappers::inline::bool::Bool,
}

```
