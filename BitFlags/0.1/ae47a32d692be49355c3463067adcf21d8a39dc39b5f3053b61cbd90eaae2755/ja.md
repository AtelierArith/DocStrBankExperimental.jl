```
@bitflagx [T=FlagTypeName] BitFlagName[::BaseType] value1[=x] value2[=y]
```

[`@bitflag`](@ref) と似ていますが、新しい型 `FlagTypeName`（最初のオプション引数で上書きされない場合は `T` と名付けられます）と、モジュール名 `BitFlagName` 内のメンバー定数をスコープします。

# 例

```jldoctest scopedflags julia> @bitflagx ScopedItems apple=1 fork=2 napkin=4

julia> f(x::ScopedItems.T) = "I'm a scoped flag with value: :x" f (generic function with 1 method

julia> f(ScopedItems.apple | ScopedItems.fork) "I'm a scoped flag with value: (fork | apple)"
```
