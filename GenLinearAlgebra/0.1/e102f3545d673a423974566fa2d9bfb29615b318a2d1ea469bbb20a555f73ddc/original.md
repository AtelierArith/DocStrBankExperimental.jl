`bigcell_decomposition(M [, b])`

`M`  should be a square  matrix, and `b` specifies  a block structure for a matrix  of  same  size  as  `M`  (it  is  a  `Vector`  of  `Vector`s  whose concatenation  is `1:size(M,1)`).  If `b`  is not  given, the trivial block structure `[[i] for i in axes(M,1)]` is assumed.

The  function  decomposes  `M`  as  a  product  `P₁ L P` where `P` is upper block-unitriangular   (with  identity  diagonal   blocks),  `P₁`  is  lower block-unitriangular  and `L` is block-diagonal for the block structure `b`. If  `M` is symmetric then  `P₁` is the transposed  of `P` and the result is the  pair  `[P,L]`;  else  the  result  is  the triple `[P₁,L,P]`. The only condition  for  this  decomposition  of  `M`  to  be  possible  is that the principal  minors  according  to  the  block  structure be invertible. This routine  is used  in the  Lusztig-Shoji algorithm  for computing  the Green functions  and the example  below is extracted  from the computation of the Green functions for `G₂`.

```julia-repl
julia> using LaurentPolynomials

julia> @Pol q
Pol{Int64}: q

julia> M=[q^6 q^0 q^3 q^3 q^5+q q^4+q^2; q^0 q^6 q^3 q^3 q^5+q q^4+q^2; q^3 q^3 q^6 q^0 q^4+q^2 q^5+q; q^3 q^3 q^0 q^6 q^4+q^2 q^5+q; q^5+q q^5+q q^4+q^2 q^4+q^2 q^6+q^4+q^2+1 q^5+2*q^3+q; q^4+q^2 q^4+q^2 q^5+q q^5+q q^5+2*q^3+q q^6+q^4+q^2+1]
6×6 Matrix{Pol{Int64}}:
 q⁶     1      q³     q³     q⁵+q        q⁴+q²
 1      q⁶     q³     q³     q⁵+q        q⁴+q²
 q³     q³     q⁶     1      q⁴+q²       q⁵+q
 q³     q³     1      q⁶     q⁴+q²       q⁵+q
 q⁵+q   q⁵+q   q⁴+q²  q⁴+q²  q⁶+q⁴+q²+1  q⁵+2q³+q
 q⁴+q²  q⁴+q²  q⁵+q   q⁵+q   q⁵+2q³+q    q⁶+q⁴+q²+1

julia> bb=[[2],[4],[6],[3,5],[1]];

julia> (P,L)=bigcell_decomposition(M,bb);

julia> P
6×6 Matrix{Pol{Int64}}:
 1    0  0    0    0        0
 q⁻⁶  1  q⁻³  q⁻³  q⁻¹+q⁻⁵  q⁻²+q⁻⁴
 0    0  1    0    0        0
 q⁻³  0  0    1    q⁻²      q⁻¹
 q⁻¹  0  0    0    1        0
 q⁻²  0  q⁻¹  0    q⁻¹      1

julia> L
6×6 Matrix{Pol{Int64}}:
 q⁶-q⁴-1+q⁻²  0   0            0     0            0
 0            q⁶  0            0     0            0
 0            0   q⁶-q⁴-1+q⁻²  0     0            0
 0            0   0            q⁶-1  0            0
 0            0   0            0     q⁶-q⁴-1+q⁻²  0
 0            0   0            0     0            q⁶-1

julia> M==transpose(P)*L*P
true
```
