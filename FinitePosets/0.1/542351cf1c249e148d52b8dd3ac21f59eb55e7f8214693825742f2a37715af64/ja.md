`dual(P)`

`Poset`または`CPoset`の双対順序集合（順序関係が逆転します）。

```julia-repl
julia> p=CPoset((i,j)->i%4<j%4,8)
4,8<1,5<2,6<3,7

julia> dual(p)
3,7<2,6<1,5<4,8
```
