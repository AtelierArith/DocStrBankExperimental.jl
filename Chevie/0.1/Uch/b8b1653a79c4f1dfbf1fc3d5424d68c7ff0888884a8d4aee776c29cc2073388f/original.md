`lusztig_induce(W,u)`

`u`  should be a unipotent character of a parabolic subcoset of the Coxeter coset  `W`. It represents  a unipotent character  `λ` of a  Levi `𝐋` of the algebraic  group  `𝐆`  attached  to  `W`.  The  program returns the Lusztig induced $R_𝐋^𝐆(λ)$.

```julia-repl
julia> W=coxgroup(:G,2)
G₂

julia> WF=spets(W)
G₂

julia> T=subspets(WF,Int[],W(1))
G₂₍₎=Φ₁Φ₂

julia> u=unichar(T,1)
[G₂₍₎=Φ₁Φ₂]:<Id>

julia> lusztig_induce(WF,u)
[G₂]:<φ₁‚₀>-<φ₁‚₆>-<φ′₁‚₃>+<φ″₁‚₃>

julia> dlchar(W,W(1))
[G₂]:<φ₁‚₀>-<φ₁‚₆>-<φ′₁‚₃>+<φ″₁‚₃>
```
