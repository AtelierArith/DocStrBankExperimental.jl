`AsymptoticAlgebra(W,i)`

The  asymptotic algebra `A` associated to  the algebra `H=Hecke(W,q)` is an algebra   with   basis   $\{tₓ\}_{x∈   W}$   and   structure  constants $t_xt_y=\sum_z  γ_{x,y,z}  t_z$  given  by:  let  $h_{x,y,z}$  be  the coefficient  of  $C_x  C_y$  on  $C_z$. Then $h_{x,y,z}=γ_{x,y,z^{-1}} q^{a(z)/2}+$lower terms, where $q^{a(z)/2}$ is the maximum over `x,y` of the degree of $h_{x,y,z}$.

The  algebra `A`  is the  direct product  of the subalgebras $A_{\mathcal C}$  generated  by  the  elements  $\{t_x\}_{x∈{\mathcal  C}}$, where $\mathcal C$ runs over the two-sided cells of `W`. If $\mathcal C$ is the  `i`-th  two-sided  cell  of  `W`, the command `AsymptoticAlgebra(W,i)` returns  the algebra $A_{\mathcal C}$. Note  that the function `a(z)` is constant  over  a  two-sided  cell,  equal  to  the  common value of the `a`-function   attached  to  the  characters   of  the  two-sided  cell  (see `Character` for left cells).

```julia-repl
julia> W=coxgroup(:G,2)
G₂

julia> A=AsymptoticAlgebra(W,1)
AsymptoticAlgebra(G₂,1) dim.10

julia> b=basis(A)
10-element Vector{AlgebraElt{AsymptoticAlgebra, Int64}}:
 t₂
 t₁₂
 t₂₁₂
 t₁₂₁₂
 t₂₁₂₁₂
 t₁
 t₂₁
 t₁₂₁
 t₂₁₂₁
 t₁₂₁₂₁

julia> b*permutedims(b)
10×10 Matrix{AlgebraElt{AsymptoticAlgebra, Int64}}:
 t₂      0            t₂₁₂            …  0               t₂₁₂₁        0
 t₁₂     0            t₁₂+t₁₂₁₂          0               t₁₂₁+t₁₂₁₂₁  0
 t₂₁₂    0            t₂+t₂₁₂+t₂₁₂₁₂     0               t₂₁+t₂₁₂₁    0
 t₁₂₁₂   0            t₁₂+t₁₂₁₂          0               t₁+t₁₂₁      0
 t₂₁₂₁₂  0            t₂₁₂               0               t₂₁          0
 0       t₁₂          0               …  t₁₂₁            0            t₁₂₁₂₁
 0       t₂+t₂₁₂      0                  t₂₁+t₂₁₂₁       0            t₂₁₂₁
 0       t₁₂+t₁₂₁₂    0                  t₁+t₁₂₁+t₁₂₁₂₁  0            t₁₂₁
 0       t₂₁₂+t₂₁₂₁₂  0                  t₂₁+t₂₁₂₁       0            t₂₁
 0       t₁₂₁₂        0                  t₁₂₁            0            t₁

julia> CharTable(A)
CharTable(AsymptoticAlgebra(G₂,1) dim.10)
┌─────┬───────────────────────────────────────┐
│     │2 12 212 1212 21212 1 21 121 2121 12121│
├─────┼───────────────────────────────────────┤
│φ′₁‚₃│.  .   .    .     . 1  .  -1    .     1│
│φ₂‚₁ │1  .   2    .     1 1  .   2    .     1│
│φ₂‚₂ │1  .   .    .    -1 1  .   .    .    -1│
│φ″₁‚₃│1  .  -1    .     1 .  .   .    .     .│
└─────┴───────────────────────────────────────┘
```
