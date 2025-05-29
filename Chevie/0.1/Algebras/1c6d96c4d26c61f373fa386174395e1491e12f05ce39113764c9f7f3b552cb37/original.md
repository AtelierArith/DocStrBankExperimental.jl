'SolomonAlgebra(W,K)'

Let  `(W,S)` be a  finite Coxeter group.  If `w` is  an element of `W`, let `R(w)={s  ∈ S | l(ws) >  l(w)}`. If `I` is a  subset of `S`, we set `Y_I={w ∈ W | R(w)=I}`, `X_I={w ∈ W | R(w) ⊃ I}`.

Note  that `X_I` is the set of minimal length left coset representatives of `W/W_I`. Now, let `y_I=∑_{w ∈ Y_I} w`, `x_I=∑_{w ∈ X_I} w`.

They  are elements  of the  group algebra  `ℤ W`  of `W` over `Z`. Now, let $Σ(W)  = ⊕_{I ⊂ S} ℤ y_I = ⊕_{I ⊂ S} ℤ x_I$. This is a sub-`ℤ`-module of `ℤW`.  In fact, Solomon proved  that it is a  sub-algebra of `ℤW`. Now, let `K(W)`  be the Grothendieck ring  of `W` and let  `θ:Σ(W)→ K(W)` be the map defined  by  `θ(x_I)  =  Ind_{W_I}^W  1`.  Solomon  proved  that this is an homomorphism of algebras. We call it the *Solomon homomorphism*.

returns  the Solomon  descent algebra  of the  finite Coxeter group `(W,S)` over  `K`.  If  `S=[s₁,…,sᵣ]`,  the  element `x_I` corresponding to the subset   `I=[s₁,s₂,s₄]`  of  `S`  is  printed  as  |X(124)|.  Note  that 'A:=SolomonAlgebra(W,K)' is endowed with the following fields:

'A.W': the group `W`

'A.basis': the basis `(x_I)_{I ⊂ S}`.

'A.xbasis':  the function sending the subset `I` (written as a number: for instance `124` for `[s_1,s_2,s_4]`) to `x_I`.

'A.ybasis': the function sending the subset `I` to `y_I`.

'A.injection':  the injection of `A` in the group algebra of `W`, obtained by calling 'SolomonAlgebraOps.injection(A)'.

Note that 'SolomonAlgebra(W,K)' endows `W` with the field `W.solomon` which is a record containing the following fields:

'W.solomon_subsets': the set of subsets of `S`

'W.solomon*conjugacy':  conjugacy classes  of parabolic  subgroups of `W` (a conjugacy   class  is  represented  by  the   list  of  the  positions,  in 'W.solomon.subsets', of the subsets `I` of `S` such that `W*I` lies in this conjugacy class).

'W.solomon_mackey':  essentially  the  structure  constants  of  the Solomon algebra over the rationals.

```julia-repl
julia> W=coxgroup(:B,4)
B₄

julia> A=SolomonAlgebra(W)
SolomonAlgebra(B₄,Int64)

julia> X=A.xbasis; X(1,2,3)*X(2,4)
2X₂+2X₄

julia> W.solomon_subsets
16-element Vector{Vector{Int64}}:
 [1, 2, 3, 4]
 [1, 2, 3]
 [1, 2, 4]
 [1, 3, 4]
 [2, 3, 4]
 [1, 2]
 [1, 3]
 [1, 4]
 [2, 3]
 [2, 4]
 [3, 4]
 [1]
 [2]
 [3]
 [4]
 []

julia> W.solomon_conjugacy
12-element Vector{Vector{Int64}}:
 [1]
 [2]
 [3]
 [4]
 [5]
 [6]
 [7, 8]
 [9, 11]
 [10]
 [12]
 [13, 14, 15]
 [16]

julia> Algebras.injection(A)(X(1,2,3))
e_+e₄+e₃₄+e₂₃₄+e₁₂₃₄+e₂₁₂₃₄+e₃₂₁₂₃₄+e₄₃₂₁₂₃₄
```
