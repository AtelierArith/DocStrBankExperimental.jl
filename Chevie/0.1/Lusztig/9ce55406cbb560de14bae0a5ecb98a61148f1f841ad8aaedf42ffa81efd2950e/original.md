`lusztig_induction_table(R,W)`

`R`  should be a parabolic subgroup of the Coxeter group `W` or a parabolic subcoset  of  the  Coxeter  coset  `W`,  in  each  case representing a Levi subgroup  `𝐋` of  the algebraic  group `𝐆`  associated to `W`. The function returns  an `InductionTable`  representing the  Lusztig induction $R_𝐋^𝐆$ between unipotent characters.

```julia-repl
julia> W=coxgroup(:B,3)
B₃

julia> t=twistings(W,[1,3])
2-element Vector{Spets{FiniteCoxeterSubGroup{Perm{Int16},Int64}}}:
 B₃₍₁₃₎=Ã₁×A₁Φ₁
 B₃₍₁₃₎=Ã₁×A₁Φ₂

julia> lusztig_induction_table(t[2],W)
Lusztig induction from B₃₍₁₃₎=Ã₁×A₁Φ₂ to B₃
┌─────┬───────────────────────┐
│     │11⊗ 11 11⊗ 2 2⊗ 11 2⊗ 2│
├─────┼───────────────────────┤
│111. │     1    -1    -1    .│
│11.1 │    -1     .     1   -1│
│1.11 │     .     .    -1    .│
│.111 │    -1     .     .    .│
│21.  │     .     .     .    .│
│1.2  │     1    -1     .    1│
│2.1  │     .     1     .    .│
│.21  │     .     .     .    .│
│3.   │     .     .     .    1│
│.3   │     .     1     1   -1│
│B₂:2 │     .     .     1   -1│
│B₂:11│     1    -1     .    .│
└─────┴───────────────────────┘
```
