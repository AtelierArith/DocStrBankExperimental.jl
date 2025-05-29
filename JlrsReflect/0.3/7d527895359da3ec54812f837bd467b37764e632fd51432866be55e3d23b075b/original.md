```
reflect(types::Vector{<:Type}; f16::Bool=false, internaltypes::Bool=false)::Wrappers
```

Generate Rust wrappers for all types in `types` and their dependencies. The only requirement is that these types must not contain any union or tuple fields that depend on a type parameter. Wrappers are generated for the most general case by erasing the contents of all provided type parameters, so you can't avoid this restriction by explicitly providing a more qualified type. The only effect qualifying types has, is that wrappers for the used parameters will also be generated. The wrappers will derive `Unbox` and `ValidLayout`, and `IntoJulia` if it's a bits-type with no type parameters.

Some types are only available in jlrs if the `internal-types` feature is enabled, if you've enabled this feature you can set the `internaltypes` keyword argument to `true` to make use of these provided wrappers in the unlikely case that the types you're reflecting depend on them. Similarly, the `Float16` type can only be reflected when the `f16` feature is enabled in jlrs and the `f16` keyword argument is set to `true`.

The result of this function can be written to a file, its contents will normally be a valid Rust module.

When you use these wrappers with jlrs, these types must be available with the same path. For example, if you generate wrappers for `Main.Bar.Baz`, this type must be available through that exact path and not some other path like `Main.Foo.Bar.Baz`.

# Example

```jldoctest
julia> using JlrsReflect

julia> reflect([Complex])
#[repr(C)]
#[derive(Clone, Debug, Unbox, ValidLayout, ValidField, Typecheck)]
#[jlrs(julia_type = "Base.Complex")]
pub struct Complex<T>
where
    T: ::jlrs::layout::valid_layout::ValidField + Clone,
{
    pub re: T,
    pub im: T,
}
```
