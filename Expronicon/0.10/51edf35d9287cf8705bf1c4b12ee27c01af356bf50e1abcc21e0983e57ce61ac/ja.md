```
struct_name_without_inferable(def; leading_inferable::Bool=true)
```

型変数の一部が推論されることを前提としたコンストラクタ名です。詳細は[`struct_name_plain`](@ref)を参照してください。キーワード引数`leading_inferable`は、先頭の推論可能な型変数を保持するかどうかを設定するために使用できます。デフォルトは`true`で、デフォルトのJuliaコンストラクタと一貫性があります。

# 例

```julia
julia> def = @expr JLKwStruct struct Foo{N, Inferable}
    x::Inferable = 1
end

julia> struct_name_without_inferable(def)
:(Foo{N})

julia> def = @expr JLKwStruct struct Foo{Inferable, NotInferable}
    x::Inferable
end

julia> struct_name_without_inferable(def; leading_inferable=true)
:(Foo{Inferable, NotInferable})

julia> struct_name_without_inferable(def; leading_inferable=false)
:(Foo{NotInferable})
```
