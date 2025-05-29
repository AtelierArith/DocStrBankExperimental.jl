`@xcopyoverride(T, S, expr)`

Convenience macro to define `xcopy_override(tpl::T, ::FieldCopyOverride{S}) = expr`.

See [`xcopy`](@ref), [`xcopy_override`](@ref)

# Example

```julia
struct Foo
   value::Int
end

@xcopy Foo
@xcopyoverride Foo :value tpl.value / 2
```
