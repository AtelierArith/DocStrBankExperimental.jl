`WGraphToRepresentation(H::HeckeAlgebra,gr::Vector)`

`H` は、`rootpara` が定義されている有限コクセター群の一変数ヘッケ代数である必要があります。この関数は、W-グラフ `gr` によって定義される `H` の表現の行列を返します。

```julia-repl
julia> W=coxgroup(:H,3)
H₃

julia> H=hecke(W,Pol(:q)^2)
hecke(H₃,q²)

julia> g=Wgraph(W,3)
2-element Vector{Vector{Vector{Any}}}:
 [[2], [1, 2], [1, 3], [1, 3], [2, 3]]
 [[-1, [[1, 3], [2, 4], [3, 5], [4, 5]]]]

julia> WGraphToRepresentation(H,g)
3-element Vector{Matrix{Pol{Int64}}}:
 [q² 0 … 0 0; 0 -1 … 0 0; … ; 0 0 … -1 q; 0 0 … 0 q²]
 [-1 0 … 0 0; 0 -1 … q 0; … ; 0 0 … q² 0; 0 0 … q -1]
 [q² 0 … 0 0; 0 q² … 0 0; … ; 0 q … -1 0; 0 0 … 0 -1]
```
