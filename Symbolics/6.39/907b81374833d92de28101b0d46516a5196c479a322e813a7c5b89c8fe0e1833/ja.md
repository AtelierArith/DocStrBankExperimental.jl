```
tosymbol(x::Union{Num,Symbolic}; states=nothing, escape=true) -> Symbol
```

`x`をシンボルに変換します。`states`はシステムの状態であり、`escape`はターゲットに`val"y(t)"`のようなエスケープがあるかどうかを意味します。`escape`がfalseの場合、`y(t)`の代わりに`y`のみが出力されます。

# 例

```jldoctest
julia> @variables t z(t)
2-element Vector{Num}:
    t
 z(t)

julia> Symbolics.tosymbol(z)
Symbol("z(t)")

julia> Symbolics.tosymbol(z; escape=false)
:z
```
