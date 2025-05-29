```
@delete obj_optic
```

オプティックを定義し、それに対して[`delete`](@ref)を呼び出します。

```jldoctest
julia> using Accessors

julia> xs = (1,2,3);

julia> ys = @delete xs[2]
(1, 3)
```

[`@optic`](@ref)と同じ構文をサポートします。詳細は[`@set`](@ref)を参照してください。
