```
allkinds(type)
```

`@compact_structs`または`@sum_structs`で定義された全体的な型に関連付けられたすべての種類を含む`Tuple`を返します：

```julia
julia> @compact_structs AB begin
           struct A x::Int end
           struct B y::Int end
       end

julia> allkinds(AB)
(:A, :B)
```
