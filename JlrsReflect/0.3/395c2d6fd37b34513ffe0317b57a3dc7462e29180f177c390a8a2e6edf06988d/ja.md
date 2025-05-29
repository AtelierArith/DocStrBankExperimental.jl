```
renamestruct!(wrappers::Wrappers, type::Type, rename::String)
```

構造体の名前を変更します。これは、構造体の名前が無効なRustコードを引き起こしたり、警告を引き起こしたりする場合に便利です。

# 例

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
