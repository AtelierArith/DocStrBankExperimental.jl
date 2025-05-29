'abelianpart(u::UnipotentElement)'

If  `𝐔` is the unipotent subgroup and `D(𝐔)` its derived subgroup, this function   returns  the  projection   of  the  unipotent   element  'u'  on `𝐔/D(𝐔)`, that is its coefficients on the simple roots.

```julia-repl
julia> U=UnipotentGroup(coxgroup(:G,2));@Mvp x,y

julia> u=U(2=>y,1=>x)
u1(x)u2(y)u3(-xy)u4(xy²)u5(-xy³)u6(2x²y³)

julia> abelianpart(u)
u1(x)u2(y)
```
