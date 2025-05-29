```
insert(obj, optic, val)
```

`optic` に従って `obj` に値 `val` を挿入します。

呼び出し可能な `optic` に対して、この法則は `insert` 操作を定義します: `optic(insert(obj, optic, val)) == val` （適切な等価性の概念に対して）。

```jldoctest
julia> using Accessors

julia> obj = (a=1, b=2); lens=@optic _.c; val = 100;

julia> insert(obj, lens, val)
(a = 1, b = 2, c = 100)
```

他にも [`set`](@ref), [`delete`](@ref) を参照してください。
