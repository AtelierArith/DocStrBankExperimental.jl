```
set(obj, optic, val)
```

`obj`の`optic`に従って一部を`val`で置き換えます。

呼び出し可能な`optic`の場合、この法則は`set`操作を定義します：`optic(set(obj, optic, val)) == val`（適切な等価性の概念に対して）。

```jldoctest
julia> using Accessors

julia> obj = (a=1, b=2); lens=@optic _.a; val = 100;

julia> set(obj, lens, val)
(a = 100, b = 2)

julia> lens = Elements();

julia> set(obj, lens, val)
(a = 100, b = 100)
```

[`modify`](@ref)も参照してください。
