```
@insert assignment
```

修正された深くネストされたオブジェクトのコピーを返します。

# 例

```jldoctest
julia> using Accessors

julia> t = (a=1, b=2);

julia> @insert t.c = 5
(a = 1, b = 2, c = 5)

julia> t
(a = 1, b = 2)
```

[`@optic`](@ref)と同じ構文をサポートしています。 [`@set`](@ref)も参照してください。
