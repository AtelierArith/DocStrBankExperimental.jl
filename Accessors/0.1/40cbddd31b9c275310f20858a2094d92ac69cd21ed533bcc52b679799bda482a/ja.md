```
modify(f, obj, optic)
```

`obj`の一部`x`を`f(x)`で置き換えます。`optic`引数はどの部分を置き換えるかを選択します。

```jldoctest
julia> using Accessors

julia> obj = (a=1, b=2); optic=@optic _.a; f = x -> "hello $x";

julia> modify(f, obj, optic)
(a = "hello 1", b = 2)
```

詳細は[`set`](@ref)を参照してください。
