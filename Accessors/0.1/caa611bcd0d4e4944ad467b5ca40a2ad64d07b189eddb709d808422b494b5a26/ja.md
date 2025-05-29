```
delete(obj, optic)
```

`obj`の`optic`に従って部分を削除します。

`optic(delete(obj, optic))`はまだ有効な値を持つ可能性があることに注意してください：例えば、`Tuple`や`Vector`から要素を削除する場合です。

```jldoctest
julia> using Accessors

julia> obj = (a=1, b=2); lens=@optic _.a;

julia> obj_d = delete(obj, lens)
(b = 2,)

julia> lens(obj_d)
ERROR: type NamedTuple has no field a


julia> obj = (1, 2); lens=first;

julia> obj_d = delete(obj, lens)
(2,)

julia> lens(obj_d)
2
```

[`set`](@ref)や[`insert`](@ref)も参照してください。
