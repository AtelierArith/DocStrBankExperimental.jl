`decompose(w,u::UnipotentElement)`

`w`  should be an element of the Weyl group corresponding to `u`. If `𝐔` is the  unipotent radical  of the  Borel subgroup  determined by  the positive roots,  and `𝐔⁻` the  opposite unipotent radical,  this function decomposes `u` into its component in `𝐔 ∩ ʷ𝐔⁻` and its component in `𝐔 ∩ ʷ𝐔`.

```julia-repl
julia> W=coxgroup(:G,2)
G₂

julia> U=UnipotentGroup(W);@Mvp x,y

julia> u=U(2=>y,1=>x)
u1(x)u2(y)u3(-xy)u4(xy²)u5(-xy³)u6(2x²y³)

julia> decompose(W(1),u)
2-element Vector{UnipotentElement{Mvp{Int64, Int64}}}:
 u1(x)
 u2(y)u3(-xy)u4(xy²)u5(-xy³)u6(2x²y³)

julia> decompose(W(2),u)
2-element Vector{UnipotentElement{Mvp{Int64, Int64}}}:
 u2(y)
 u1(x)
```
