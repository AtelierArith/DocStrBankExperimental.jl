`almost_character(W,i)` or `almostchar(W,i)`

This  function  returns  the  `i`-th  almost  unipotent  character  of  the algebraic  group 𝐆 associated to the Coxeter group or Coxeter coset `W`. If `φ` is the `i`-th irreducible character of `W`, the `i`-th almost character is  $R_φ=W⁻¹∑_{w∈ W}  φ(w) R_{𝐓_w}^𝐆  (1)$ where  $𝐓_w$ is  the maximal torus  associated  to  the  conjugacy  class  (or `ϕ`-conjugacy class for a coset) of `w`.

```julia-repl
julia> W=coxgroup(:B,2)
B₂

julia> almostchar(W,3)
[B₂]:<.11>

julia> almostchar(W,1)
[B₂]:1//2<11.>+1//2<1.1>-1//2<.2>-1//2<B₂>
```
