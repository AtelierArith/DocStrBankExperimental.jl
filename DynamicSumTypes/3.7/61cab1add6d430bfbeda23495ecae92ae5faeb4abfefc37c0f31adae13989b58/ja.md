```
allkinds(type)
```

`@sum_structs`で定義された包括的な型に関連付けられたすべての種類を含む`Tuple`を返します。

```julia
julia> @sum_structs AB begin
           struct A x::Int end
           struct B y::Int end
       end

julia> allkinds(AB)
(:A, :B)
```
