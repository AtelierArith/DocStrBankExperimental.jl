`cartan(type, rank [,bond])`

the  Cartan matrix for a  finite Coxeter group described  by type and rank. The  recognized types are `:A, :B, :Bsym, :C, :D, :E, :F, :Fsym, :G, :Gsym, :I,  :H`. For type `:I` a third  argument must be given describing the bond between the two generators. The `sym` types correspond to (non-crystallographic)  root systems where all  roots have the same length; they  afford automorphisms that  the crystallographic root  system does not afford, which allow to define the "very twisted" Chevalley groups.

```julia-repl
julia> cartan(:F,4)
4×4 Matrix{Int64}:
  2  -1   0   0
 -1   2  -1   0
  0  -2   2  -1
  0   0  -1   2

julia> cartan(:I,2,5)
2×2 Matrix{Cyc{Int64}}:
       2  ζ₅²+ζ₅³
 ζ₅²+ζ₅³        2

julia> cartan(:Bsym,2)
2×2 Matrix{Cyc{Int64}}:
   2  -√2
 -√2    2
```
