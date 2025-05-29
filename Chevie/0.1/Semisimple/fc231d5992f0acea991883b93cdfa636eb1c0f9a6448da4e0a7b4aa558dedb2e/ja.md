`centralizer(W,s::SemisimpleElement)`

`W` は Weyl 群または拡張反射群であり、`s` は `W` に対応する代数群 `G` の半単純要素です。この関数は $C_G(s)$ の Weyl 群を返し、それを説明します。安定化群は拡張反射群であり、反射群部分は $C_{G⁰}(s)$ の Weyl 群と等しく、図自動同型部分は $C_G(s)$ によって誘導されるものです。

```julia-repl
julia> G=coxgroup(:A,3)
A₃
julia> s=ss(G,[0,1//2,0])
SemisimpleElement{Root1}: <1,-1,1>
julia> centralizer(G,s)
A₃₍₁₃₎=(A₁A₁)Φ₂
```
