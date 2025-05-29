`xcopy(tpl, kwargs...)`

Extended `Base.copy` method which allows setting a field directly rather than copying it from `tpl`.

See also [`@xcopy`](@ref), [`xcopyargs`](@ref), [`xcopy_override`](@ref), [`xcopy_construct`](@ref).

# Example

```julia
struct Foo{A}
   a::A
end

xcopy(Foo{Int32}(24), a=42) # == Foo{Int32}(42)
```
