`cuspidal_data(W[,d[,ad]];proper=false,all=false)`

returns  named tuples `(levi=LF,cuspidal=λ,d=d)` where  `LF` is a `d`-split Levi  (with `d`-center  of dimension  `ad` if  `ad` is  given) and `λ` is a `d`-cuspidal  character of  `LF`. If  `d=1` this  returns ordinary cuspidal characters.  The  character  `λ`  is  given  as  its  index  in the list of unipotent  characters. If `d` was given as  an integer, it is returned as a `Root1` representing `E(d)`.

If  the keyword  `proper=true` is  given, only  the data  where `LF!=W` (or equivalently `ad>0`) are returned.

If  `d` is omitted, data  for all `d` orders  of eigenvalues of elements of `W`  is returned. If in addition  the keyword argument `all=true` is given, data for all eigenvalues of elements of `W` is returned.

```julia-repl
julia> cuspidal_data(coxgroup(:F,4),1)
9-element Vector{@NamedTuple{levi::Spets{FiniteCoxeterSubGroup{Perm{Int16},Int64}}, cuspidal::Int64, d::Root1}}:
 (levi = F₄, cuspidal = 31, d = 1)
 (levi = F₄, cuspidal = 32, d = 1)
 (levi = F₄, cuspidal = 33, d = 1)
 (levi = F₄, cuspidal = 34, d = 1)
 (levi = F₄, cuspidal = 35, d = 1)
 (levi = F₄, cuspidal = 36, d = 1)
 (levi = F₄, cuspidal = 37, d = 1)
 (levi = F₄₍₂₃₎=B₂₍₂₁₎Φ₁², cuspidal = 6, d = 1)
 (levi = F₄₍₎=Φ₁⁴, cuspidal = 1, d = 1)

julia> cuspidal_data(complex_reflection_group(4),3)
5-element Vector{@NamedTuple{levi::Spets{PRSG{Cyc{Rational{Int64}}, Int16}}, cuspidal::Int64, d::Root1}}:
 (levi = G₄, cuspidal = 3, d = ζ₃)
 (levi = G₄, cuspidal = 6, d = ζ₃)
 (levi = G₄, cuspidal = 7, d = ζ₃)
 (levi = G₄, cuspidal = 10, d = ζ₃)
 (levi = G₄₍₎=Φ₁Φ′₃, cuspidal = 1, d = ζ₃)
```
