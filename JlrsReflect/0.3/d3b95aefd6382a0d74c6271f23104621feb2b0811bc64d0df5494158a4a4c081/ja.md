```
renamefields!(wrappers::Wrappers, type::Type, rename::Dict{Symbol,String})
renamefields!(wrappers::Wrappers, type::Type, rename::Vector{Pair{Symbol,String})
```

構造体のいくつかのフィールド名を変更します。これは、構造体の名前が無効なRustコードを引き起こしたり、警告を引き起こしたりする場合に便利です。

# 例

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
