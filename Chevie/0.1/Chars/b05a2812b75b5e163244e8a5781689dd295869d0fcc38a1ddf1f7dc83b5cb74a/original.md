`J_induction_table(H, W)`

computes  the decomposition  into irreducible  characters of the reflection group  `W`  of  the  `J`-induced  of  the  irreducible  characters  of  the reflection  subgroup  `H`.  The  `J`-induced  of  `φ`  is  the  sum  of the irreducible  components of the induced of  `φ` which have same `a`-function (see `charinfo`) as `φ`. What is returned is an `InductionTable` struct.

```julia-repl
julia> W=coxgroup(:D,4)
D₄

julia> H=reflection_subgroup(W,[1,3])
D₄₍₁₃₎=A₂Φ₁²

julia> J_induction_table(H,W)
J-induction table from D₄₍₁₃₎=A₂Φ₁² to D₄
┌─────┬────────┐
│     │111 21 3│
├─────┼────────┤
│11+  │  .  . .│
│11-  │  .  . .│
│1.111│  .  . .│
│.1111│  .  . .│
│11.2 │  1  . .│
│1.21 │  1  . .│
│.211 │  .  . .│
│2+   │  .  . .│
│2-   │  .  . .│
│.22  │  .  . .│
│1.3  │  .  1 .│
│.31  │  .  . .│
│.4   │  .  . 1│
└─────┴────────┘
```
