'abelianpart(u::UnipotentElement)'

もし `𝐔` がユニポテント部分群であり、`D(𝐔)` がその導来群であるなら、この関数はユニポテント要素 'u' の `𝐔/D(𝐔)` への射影、すなわち単純根に対するその係数を返します。

```julia-repl
julia> U=UnipotentGroup(coxgroup(:G,2));@Mvp x,y

julia> u=U(2=>y,1=>x)
u1(x)u2(y)u3(-xy)u4(xy²)u5(-xy³)u6(2x²y³)

julia> abelianpart(u)
u1(x)u2(y)
```
