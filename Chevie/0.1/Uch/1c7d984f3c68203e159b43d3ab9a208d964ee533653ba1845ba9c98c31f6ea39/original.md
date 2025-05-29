`degrees(uc::UnipotentCharacters,q=Pol())`

Returns  the  list  of  degrees  of  the unipotent characters of the finite reductive group (or Spetses) with Weyl group (or Spetsial reflection group) `W`, evaluated at `q`.

```julia-repl
julia> W=coxgroup(:G,2)
G₂

julia> uc=UnipotentCharacters(W);

julia> degrees(uc)
10-element Vector{Pol{Rational{Int64}}}:
 1
 q⁶
 (1//3)q⁵+(1//3)q³+(1//3)q
 (1//3)q⁵+(1//3)q³+(1//3)q
 (1//6)q⁵+(1//2)q⁴+(2//3)q³+(1//2)q²+(1//6)q
 (1//2)q⁵+(1//2)q⁴+(1//2)q²+(1//2)q
 (1//2)q⁵+(-1//2)q⁴+(-1//2)q²+(1//2)q
 (1//6)q⁵+(-1//2)q⁴+(2//3)q³+(-1//2)q²+(1//6)q
 (1//3)q⁵+(-2//3)q³+(1//3)q
 (1//3)q⁵+(-2//3)q³+(1//3)q
```
