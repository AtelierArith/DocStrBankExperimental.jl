`representation(H::HeckeAlgebra or HeckeCoset,i)`

は、Hecke代数またはHeckeコセット `H` の `i` 番目の不可約表現の行列のリストを返します。これは、表現のモデルにおける `H` の生成子の画像です（Heckeコセットの場合、結果は `gens`、`hecke(H)` の表現、そして表現における `H` の自己同型の行列 `F` を持つ `NamedTuple` です）。

この関数は分類に基づいており、グループ `G₃₁`、`G₃₂`、および `G₃₄` のHecke代数に対してはまだ完全には実装されていません：タイプ `G₃₁` については59のうち50の表現、タイプ `G₃₂` については102のうち30の表現、タイプ `G₃₄` については169のうち38の表現があります；欠落している表現には `nothing` が返されます。

```julia-repl
julia> W=crg(24)
G₂₄

julia> H=hecke(W,Pol(:q))
hecke(G₂₄,q)

julia> representation(H,3)
3-element Vector{Matrix{Pol{Cyc{Int64}}}}:
 [q 0 0; -q -1 0; -q 0 -1]
 [-1 0 -1; 0 -1 ((1-√-7)/2)q; 0 0 q]
 [-1 -1 0; 0 q 0; 0 (1+√-7)/2 -1]
```

`n>2` および `de>1` の非原始的タイプ `G(de,e,n)` に対して実装されたモデル（Coxeterタイプ `Dₙ` を含む）は、`G(2,2,4)、G(3,3,3)、G(3,3,4)、G(3,3,5)` および `G(4,4,3)` を除いて、有理数の分数を含みます。

```julia-repl
julia> H=hecke(coxgroup(:D,5),Pol())
hecke(D₅,q)

julia> representation(H,7)
5-element Vector{Matrix{Frac{Pol{Int64}}}}:
 [q 0 0 0; 0 -1 0 0; 0 0 -1 0; 0 0 0 -1]
 [q 0 0 0; 0 -1 0 0; 0 0 -1 0; 0 0 0 -1]
 [1/(-q-1) q/(q+1) 0 0; (q²+q+1)/(q+1) q²/(q+1) 0 0; 0 0 -1 0; 0 0 0 -1]
 [-1 0 0 0; 0 1/(-q²-q-1) (-q²-q)/(-q²-q-1) 0; 0 (q³+q²+q+1)/(q²+q+1) q³/(q²+q+1) 0; 0 0 0 -1]
 [-1 0 0 0; 0 -1 0 0; 0 0 1/(-q³-q²-q-1) (-q³-q²-q)/(-q³-q²-q-1); 0 0 (q⁴+q³+q²+q+1)/(q³+q²+q+1) q⁴/(q³+q²+q+1)]
```
