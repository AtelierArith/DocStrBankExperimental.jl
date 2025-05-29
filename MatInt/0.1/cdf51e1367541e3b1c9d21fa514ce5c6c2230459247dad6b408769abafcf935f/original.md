`smith_transforms(m::AbstractMatrix{<:Integer})`

The  Smith normal form of `m` is  the unique equivalent diagonal matrix `S` such  that `Sᵢ,ᵢ` divides `Sⱼ,ⱼ` for  `i≤j`. There exist unimodular integer matrices  `c,  r`  such  that  `r*m*c==S`.  The function `smith_transforms` returns  a  named  tuple  with  components  `.normal=S`,  `.rowtrans=r` and `.coltrans=c`.

```julia-repl
julia> m=[1 15 28 7;4 5 6 7;7 8 9 7]
3×4 Matrix{Int64}:
 1  15  28  7
 4   5   6  7
 7   8   9  7

julia> n=smith_transforms(m)
(normal = [1 0 0 0; 0 1 0 0; 0 0 3 0], coltrans = [1 0 -1 -84; 0 1 -1 175; 0 0 1 -91; 0 0 0 1], rowtrans = [-2 62 -35; 1 -30 17; -3 97 -55], rank = 3, signdet = nothing)

julia> n.rowtrans*m*n.coltrans==n.normal
true
```
