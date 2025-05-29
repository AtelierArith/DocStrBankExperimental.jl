`xcopy_override(tpl, ::FieldCopyOverride{S}) where S`

`tpl`内のフィールド`S`のコピーされた値を定義します。デフォルトでは`Base.copy(getproperty(tpl, S))`です。

関連情報は[`xcopy`](@ref)を参照してください。

# 例

```julia
struct Foo
    value::Int
end

struct Bar
    foo::Foo
end

xcopy_override(bar::Bar, ::FieldCopyOverride{:foo}) = Foo(bar.foo.value + 1)
xcopy(Bar(Foo(24))) # == Bar(Foo(25))
```
