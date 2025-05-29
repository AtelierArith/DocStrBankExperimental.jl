'U(r)'

'U(r*1=>c*1`,..,r_n=>c_n`)'

Where `U` is a `UnipotentGroup`. In the first form the function creates the element  `uᵣ(1)`,  and  in  the  second  form  the  element  `u_{r_1}(c_1)… u_{r_n}(c_n)`

```julia-repl
julia> U=UnipotentGroup(coxgroup(:G,2))
UnipotentGroup(G₂)

julia> U(2)
u2(1)

julia> U(1=>2,2=>4)
u1(2)u2(4)

julia> U(2=>4,1=>2)
u1(2)u2(4)u3(-8)u4(32)u5(-128)u6(512)
```
