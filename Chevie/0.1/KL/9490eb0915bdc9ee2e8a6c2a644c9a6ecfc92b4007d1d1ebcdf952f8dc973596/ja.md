`AsymptoticAlgebra(W,i)`

代数 `H=Hecke(W,q)` に関連する漸近代数 `A` は、基底 $\{tₓ\}_{x∈ W}$ を持ち、構造定数 $t_xt_y=\sum_z  γ_{x,y,z}  t_z$ によって与えられます。ここで、$h_{x,y,z}$ は $C_x  C_y$ の $C_z$ に対する係数です。すると、$h_{x,y,z}=γ_{x,y,z^{-1}} q^{a(z)/2}+$低次の項となり、$q^{a(z)/2}$ は $h_{x,y,z}$ の次数の `x,y` に関する最大値です。

代数 `A` は、要素 $\{t_x\}_{x∈{\mathcal C}}$ によって生成される部分代数 $A_{\mathcal C}$ の直積です。もし $\mathcal C$ が `W` の `i`-番目の両側セルであるなら、コマンド `AsymptoticAlgebra(W,i)` は代数 $A_{\mathcal C}$ を返します。関数 `a(z)` は両側セル上で定数であり、両側セルのキャラクターに付随する `a`-関数の共通値に等しいことに注意してください（左セルについては `Character` を参照）。

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
