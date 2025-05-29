`image(b::GarsideElt)`

この関数は、`b` が区間モノイドの要素である場合にのみ定義されます。たとえば、ブレイドです。これは、モノイドが区間モノイドである群における `b` の像を返します。たとえば、アーティンモノイドにおけるブレイドの射影をコクセター群に戻します。

```julia-repl
julia> W=coxsym(4)
𝔖 ₄

julia> b=BraidMonoid(W)(2,1,2,1,1)
121.1.1

julia> p=image(b)
(1,3)

julia> word(W,p)
3-element Vector{Int64}:
 1
 2
 1
```
