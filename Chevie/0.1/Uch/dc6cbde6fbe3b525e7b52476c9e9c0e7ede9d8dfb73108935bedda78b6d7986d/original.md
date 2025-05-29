`unipotent_character(W,l)` or `unichar(W,l)`

Constructs  an object representing the unipotent character specified by `l` of  the algebraic  group associated  to the  Coxeter group or Coxeter coset specified  by `W`. There are 3 possibilities  for `l`: if it is an integer, the  `l`-th unipotent character of `W` is  returned. If it is a string, the unipotent  character of `W` whose name is  `l` is returned (where the names are as given by `charnames(UnipotentCharacters(W))`). Finally, `l` can be a list  of length the number of  unipotent characters of `W`, which specifies the coefficient to give to each unipotent character.

```julia-repl
julia> W=coxgroup(:G,2)
G₂

julia> u=unichar(W,7)
[G₂]:<G₂[-1]>

julia> v=unichar(W,"G2[E3]")
[G₂]:<G₂[ζ₃]>

julia> w=unichar(W,[1,0,0,-1,0,0,2,0,0,1])
[G₂]:<φ₁‚₀>-<φ″₁‚₃>+2<G₂[-1]>+<G₂[ζ₃²]>

julia> unichar(W,fourier(UnipotentCharacters(W))[3,:])
[G₂]:2//3<φ′₁‚₃>-1//3<φ″₁‚₃>+1//3<φ₂‚₁>+1//3<G₂[1]>-1//3<G₂[ζ₃]>-1//3<G₂[ζ₃²]>
```

The  last line shows  the almost character  associated to the 3rd unipotent character of `W`.

some limited arithmetic is available on unipotent characters:

```julia-repl
julia> coefficients(u) # so that u==unichar(W,coefficients(u))
10-element Vector{Int64}:
 0
 0
 0
 0
 0
 0
 1
 0
 0
 0

julia> w-2u
[G₂]:<φ₁‚₀>-<φ″₁‚₃>+<G₂[ζ₃²]>

julia> w*w  # scalar product
7

julia> degree(w)
Pol{Int64}: q⁵-q⁴-q³-q²+q+1
```
