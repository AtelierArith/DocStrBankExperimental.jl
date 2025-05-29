`decompose(w,u::UnipotentElement)`

`w` は `u` に対応するウィール群の要素である必要があります。もし `𝐔` が正のルートによって決定されるボレル部分群の非可換根であり、`𝐔⁻` が反対の非可換根である場合、この関数は `u` を `𝐔 ∩ ʷ𝐔⁻` の成分と `𝐔 ∩ ʷ𝐔` の成分に分解します。

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
