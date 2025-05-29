```
renamestruct!(wrappers::Wrappers, type::Type, rename::String)
```

Change a struct's name. This can be useful if the name of a struct results in invalid Rust code or causes warnings.

# Example

```jldoctest
julia> using JlrsReflect

julia> struct Foo end

julia> wrappers = reflect([Foo]);

julia> renamestruct!(wrappers, Foo, "Bar")

julia> wrappers
#[repr(C)]
#[derive(Clone, Debug, Unbox, ValidLayout, ValidField, Typecheck, IntoJulia)]
#[jlrs(julia_type = "Main.Foo", zero_sized_type)]
pub struct Bar {
}
```
