`@xcopyoverride(T, S, expr)`

`tpl::T`に対して`xcopy_override(tpl::T, ::FieldCopyOverride{S}) = expr`を定義するための便利なマクロです。

[`xcopy`](@ref)、[`xcopy_override`](@ref)を参照してください。

# 例

```julia
struct Foo
   value::Int
end

@xcopy Foo
@xcopyoverride Foo :value tpl.value / 2
```
