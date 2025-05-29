`xcopy(tpl, kwargs...)`

`Base.copy` メソッドの拡張で、`tpl` からフィールドをコピーするのではなく、直接フィールドを設定することができます。

関連情報として [`@xcopy`](@ref)、[`xcopyargs`](@ref)、[`xcopy_override`](@ref)、[`xcopy_construct`](@ref) を参照してください。

# 例

```julia
struct Foo{A}
   a::A
end

xcopy(Foo{Int32}(24), a=42) # == Foo{Int32}(42)
```
