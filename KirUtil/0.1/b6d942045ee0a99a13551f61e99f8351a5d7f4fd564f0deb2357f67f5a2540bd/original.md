`xcopy_override(tpl, ::FieldCopyOverride{S}) where S`

Defines the copied value of field `S` in `tpl`. Defaults to `Base.copy(getproperty(tpl, S))`.

See also [`xcopy`](@ref).

# Example

```julia struct Foo    value::Int end

struct Bar    foo::Foo end

xcopy_override(bar::Bar, ::FieldCopyOverride{:foo}) = Foo(bar.foo.value + 1) xcopy(Bar(Foo(24))) # == Bar(Foo(25))
