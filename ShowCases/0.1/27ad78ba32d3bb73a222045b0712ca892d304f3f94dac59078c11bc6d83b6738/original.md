```
ShowCase(o, props=propertynames(o);
         type_style=Style(), show_module=:context,
         max_params=3, show_params=true, kw...)
```

Creates and `AbstractShow` object which combines all elements used in default `show` methods.  This concatenates [`ShowTypeOf`](@ref) and [`ShowProps`](@ref).

## Arguments

  * `o`: object to be wrapped.
  * `props`: properties of the object to be shown.
  * `type_style`: Style to be used for the type.
  * `show_module::Symbol`: whether to show the module of type and type parameters, see [`ShowType`](@ref).
  * `max_params::Integer`: maximum number of type parameters to show.
  * `show_params::Bool`: whether to show params. Note that if `max_params=0` and `show_params=true`, brackets with   continuation strings will be shown.
  * `kw`: other keyword arguments passed to [`ShowProps`](@ref).

## Examples

```
julia> ShowCase(1.0 + im)
ComplexF64{Float64}(re=1.0, im=1.0)

julia> ShowCase(1.0 + im, new_lines=true)
ComplexF64{Float64}(
    re = 1.0,
    im = 1.0
)

julia> ShowCase(1.0 + im, type_style=Style(:cyan, true), max_params=0)
ComplexF64{…}(re=1.0, im=1.0)

julia> ShowCase(1.0 + im, [:im], keyword_style=Style(:magenta))
ComplexF64{Float64}(im=1.0)
```
