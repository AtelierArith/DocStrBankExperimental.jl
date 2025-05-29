```
@modify(f, obj_optic)
```

オプティックを定義し、それに対して[`modify`](@ref)を呼び出します。

```jldoctest
julia> using Accessors

julia> xs = (1,2,3);

julia> ys = @modify(xs |> Elements() |> If(isodd)) do x
           x + 1
       end
(2, 2, 4)
```

[`@optic`](@ref)と同じ構文をサポートしています。さらに[`@set`](@ref)も参照してください。
