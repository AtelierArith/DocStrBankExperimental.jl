`representation(c::LeftCell,H)`

は、左セル `c` に対する Iwahori-Hecke 代数 `H` の表現を与える行列を返します。

```julia-repl
julia> W=coxgroup(:H,3)
H₃

julia> c=left_cells(W)[3]
LeftCell<H₃: duflo=(15) character=φ₅‚₅>

julia> @Mvp q;H=hecke(W,q)
hecke(H₃,q)

julia> representation(c,H)
3-element Vector{Matrix{Mvp{Int64, Rational{Int64}}}}:
 [-1 0 … 0 0; 0 -1 … 0 -q½; … ; 0 0 … q 0; 0 0 … 0 q]
 [-1 -q½ … 0 0; 0 q … 0 0; … ; 0 0 … -1 0; 0 -q½ … 0 -1]
 [q 0 … 0 0; -q½ -1 … 0 0; … ; 0 0 … q 0; 0 0 … 0 -1]
```
