`degrees(WF::Spets)`

Let  `W` be  the group  of the  reflection coset  `WF`, and  let `V` be the vector  space  of  dimension  `rank(W)`  on  which `W` acts as a reflection group.  Let  `f₁,…,fₙ`  be  the  basic  invariants  of `W` on the symmetric algebra  `SV` of `V`;  they can be  chosen so they  are eigenvectors of the matrix  `WF.F`. The corresponding  eigenvalues are called  the *factors* of `F` acting on `V`; they characterize the coset –- they are equal to 1 only for  the trivial  coset. The  *generalized degrees*  of `WF`  are the pairs formed of the reflection degrees and the corresponding factor.

```julia-repl
julia> W=coxgroup(:E,6)
E₆

julia> WF=spets(W)
E₆

julia> phi=W(6,5,4,2,3,1,4,3,5,4,2,6,5,4,3,1);

julia> HF=subspets(WF,2:5,phi)
E₆₍₂₃₄₅₎=³D₄Φ₃

julia> diagram(HF)
ϕ acts as (1,2,4) on the component below
  O 2
  ￨
O—O—O D₄
1 3 4

julia> degrees(HF)
6-element Vector{Tuple{Int64, Cyc{Int64}}}:
 (1, ζ₃)
 (1, ζ₃²)
 (2, 1)
 (4, ζ₃)
 (6, 1)
 (4, ζ₃²)
```
