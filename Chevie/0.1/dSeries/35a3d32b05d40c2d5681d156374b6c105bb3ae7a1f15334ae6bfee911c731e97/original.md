`Series(W, L, cuspidal, d)`

If the reflection coset or group `W` corresponds to the algebraic group `𝐆` and  `cuspidal`  to  the  `d`-cuspidal  unipotent  character  `λ`  of  `𝐋`, constructs  the `d`-series corresponding to $R_𝐋^𝐆(λ)$. The result `s` it is a record with the following fields and functions:

`s.spets`: the reflection group or coset `W`.

`s.levi`: the subcoset `L`.

`s.cuspidal`: the index of `λ` in `UnipotentCharacters(L)`.

`s.d`: the value of `d` (a `Root1`).

`relative_group(s)`: the group $W_𝐆(𝐋,λ)$.

`dSeries.RLG(s)`: the `UnipotentCharacter` given by $R_𝐋^𝐆(λ)$.

`dSeries.eps(s)`:  for each  character `φ`  of `relative_group(s)` the sign $(-1)^{n_φ}$  in the cohomology  of the variety  defining `RLG(s)` of the corresponding constituent `γᵩ` of `RLG(s)`.

`degree(s)`: the generic degree of `RLG(s)`, as a `CycPol`.

`charnumbers(s)`:  the indices in  `UnipotentCharacters(W)` of the constituents of `RLG(s)`.

`hecke(s)`: the hecke algebra $H_𝐆(𝐋,λ)$.

The function `Series` has another form:

`Series(<W> [,<d> [,<ad>]];k...)`

where  it returns a  vector of `Series`  corresponding to the cuspidal data described   by  the   arguments  and   the  keywords   (see  the  help  for `cuspidal_data`).

```julia-repl
julia> W=complex_reflection_group(4)
G₄

julia> Series(W,3;proper=true)
1-element Vector{Series}:
 ζ₃-series R^G₄_{G₄₍₎=Φ₁Φ′₃}(λ==Id)  W_G(L,λ)==Z₆

julia> s=Series(W,3,1)[1]
ζ₃-series R^G₄_{G₄₍₎=Φ₁Φ′₃}(λ==Id)  W_G(L,λ)==Z₆
┌─┬────────────────────────────────────┐
│ │   γᵩ φ(mod 3)  ε parameter family #│
├─┼────────────────────────────────────┤
│1│ φ₁‚₀        1  1      ζ₃q²        1│
│5│ φ₂‚₃       ζ₆  1      -ζ₃q        2│
│2│ φ₁‚₄       ζ₃ -1        ζ₃        4│
│8│ Z₃:2       -1 -1     -ζ₃²q        2│
│9│Z₃:11      ζ₃² -1       ζ₃²        4│
│4│ φ₂‚₅      ζ₆⁵ -1       -ζ₃        4│
└─┴────────────────────────────────────┘

julia> s.spets
G₄

julia> s.levi
G₄₍₎=Φ₁Φ′₃

julia> s.cuspidal
1

julia> s.d
Root1: ζ₃

julia> hecke(s)
hecke(G₆‚₁‚₁,Vector{Mvp{Cyc{Int64}, Int64}}[[ζ₃q², -ζ₃q, ζ₃, -ζ₃²q, ζ₃², -ζ₃]])

julia> degree(s)
ζ₃Φ₁Φ₂²Φ″₃Φ₄Φ₆

julia> dSeries.RLG(s)
[G₄]:<φ₁‚₀>-<φ₁‚₄>-<φ₂‚₅>+<φ₂‚₃>-<Z₃:2>-<Z₃:11>

julia> charnumbers(s)
6-element Vector{Int64}:
 1
 5
 2
 8
 9
 4

julia> dSeries.eps(s)
6-element Vector{Int64}:
  1
  1
 -1
 -1
 -1
 -1

julia> relative_group(s)
G₆‚₁‚₁
```
