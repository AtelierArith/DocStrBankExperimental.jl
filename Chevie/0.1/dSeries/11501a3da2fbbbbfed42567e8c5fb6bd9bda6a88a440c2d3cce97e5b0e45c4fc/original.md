`d`-Harish-Chandra   series  describe  unipotent  `l`-blocks  of  a  finite reductive  group $𝐆(𝔽_q)$ for $l|Φ_d(q)$ (at least, when `l` is not too small which means mostly not a bad prime for `𝐆`). Some of the facts stated below  are still partly conjectural, we do not try to distinguish precisely what has been established and what is still conjectural.

If  `(𝐋,λ)` is  a `d`-cuspidal  pair then  the constituents  of the Lusztig induced  $R_𝐋^𝐆(λ)$ are called a `d`-Harish-Chandra series; they form the unipotent part of an `l`-block of $𝐆^F$. It is conjectured (and proven in some   cases)  that  the  $𝐆^F$-endomorphism   algebra  of  the  `l`-adic cohomology  of the  variety `𝐗`  which defines  the Lusztig  induction is a `d`-cyclotomic Hecke algebra $H_𝐆(𝐋,λ)$ for the group $W_𝐆(𝐋,λ):=N_𝐆(𝐋,λ)/𝐋$,  which  is  a  complex  reflection group –- here `d`-cyclotomic  means that the parameters  of $H_𝐆(𝐋,λ)$ are monomials in `q`  and that $H_𝐆(𝐋,λ)$  specializes to the  algebra of $W_𝐆(𝐋,λ)$ for $q↦ζ_d$.

It  follows that the decomposition of the  Lusztig induction is of the form $R_𝐋^𝐆(λ)=∑_{ϕ∈Irr(W_𝐆(𝐋,λ))}(-1)^{nᵩ} ϕ(1)γᵩ,$ where `γᵩ` is a unipotent character   of  `𝐆^F`  attached  to  `ϕ`  and  where  `nᵩ`  is  the  degree $H^{nᵩ}_c(𝐗)$  where  `γᵩ`  occurss;  and  further  for  any  `ϕ` we have $R_𝐋^𝐆(λ)(1)=  (-1)^{nᵩ} γᵩ(1)Sᵩ$ where `Sᵩ` is  the Schur element of the character  of  $H_𝐆(𝐋,λ)$  which  deforms  to  `ϕ`. The function |Series| allows to explore a `d`-Harish-Chandra series.

```julia-repl
julia> W=rootdatum("3D4")
³D₄

julia> l=cuspidal_data(W,3)
2-element Vector{@NamedTuple{levi::Spets{FiniteCoxeterSubGroup{Perm{Int16},Int64}}, cuspidal::Int64, d::Root1}}:
 (levi = ³D₄, cuspidal = 8, d = ζ₃)
 (levi = ³D₄₍₎=Φ₃², cuspidal = 1, d = ζ₃)

julia> Series(W,l[2]...)
ζ₃-series R^³D₄_{³D₄₍₎=Φ₃²}(λ==Id)  H_G(L,λ)==hecke(G₄,Vector{Mvp{Cyc{Int64}, Int64}}[[ζ₃q², ζ₃, ζ₃q]])
┌─┬───────────────────────┐
│ │    γᵩ    φ  ε family #│
├─┼───────────────────────┤
│1│  φ₁‚₀ φ₁‚₀  1        1│
│2│  φ₁‚₆ φ₁‚₄  1        2│
│3│  φ₂‚₂ φ₁‚₈ -1        5│
│6│ φ″₁‚₃ φ₂‚₅  1        4│
│5│ φ′₁‚₃ φ₂‚₃ -1        3│
│7│  φ₂‚₁ φ₂‚₁ -1        5│
│4│³D₄[1] φ₃‚₂  1        5│
└─┴───────────────────────┘
```

Above  we explore the 3-series corresponding  to $R_𝐓^𝐆(Id)$ where `𝐆` is the  triality group  and `𝐓`  is the  torus of  type `(q²+q+1)²`. The group $W_𝐆(𝐓)$  is the complex reflection group `G₄`. The displays shows in the column   'γᵩ'  the  name  of   the  unipotent  characters  constituents  of $R_𝐓^𝐆(Id)$,  and in the  first column the  number of these characters in the  list  of  unipotent  characters.  In  the  column  'φ' the name of the character  of $W_𝐆(𝐓)$ corresponding  to the unipotent  character `γᵩ` is shown;  in the column  'ε' we show  the sign $(-1)^{nᵩ}$.  Finally in the last column we show in which family of unipotent characters is `γᵩ`.

The theory of `d`-Harish-Chandra series can be generalized to spetsial complex reflection groups using some axioms. We show below an example.

```julia-repl
julia> W=complex_reflection_group(4)
G₄

julia> l=cuspidal_data(W,3)
5-element Vector{@NamedTuple{levi::Spets{PRSG{Cyc{Rational{Int64}}, Int16}}, cuspidal::Int64, d::Root1}}:
 (levi = G₄, cuspidal = 3, d = ζ₃)
 (levi = G₄, cuspidal = 6, d = ζ₃)
 (levi = G₄, cuspidal = 7, d = ζ₃)
 (levi = G₄, cuspidal = 10, d = ζ₃)
 (levi = G₄₍₎=Φ₁Φ′₃, cuspidal = 1, d = ζ₃)

julia> Series(W,l[5]...)
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
```

Above  we explore the `3`-series corresponding  to the trivial character of the  torus of type `(q-1)(q-ζ₃)`. For cyclic groups $W_𝐆(𝐋,λ)$ we display the  parameters in  the table  since they  are associated  to characters of $W_𝐆(𝐋,λ)$. Finally the mention '(mod 3)' which appears in the 'φ' column means that in this case the axioms leave an ambiguity in the correspondence between  unipotent  characters  `γᵩ`  and  characters  `ϕ` (as well as with parameters):  the correspondence is known only up to a translation by 3 (in this case, the same as a global multiplication of all `ϕ` by `-1`).

Finally,  we should note that  if the reflection group  or coset `W` is not defined  over the integers,  what counts is  not cyclotomic polynomials but factors  of them  over the  field of  definition of  `W`. In this case, one should not give as argument an integer `d` representing $ζ_d$ but specify a  root of unity. For instance, in the above case we get a different answer with:

```julia-repl
julia> cuspidal_data(W,E(3,2))
5-element Vector{@NamedTuple{levi::Spets{PRSG{Cyc{Rational{Int64}}, Int16}}, cuspidal::Int64, d::Root1}}:
 (levi = G₄, cuspidal = 2, d = ζ₃²)
 (levi = G₄, cuspidal = 5, d = ζ₃²)
 (levi = G₄, cuspidal = 7, d = ζ₃²)
 (levi = G₄, cuspidal = 10, d = ζ₃²)
 (levi = G₄₍₎=Φ₁Φ″₃, cuspidal = 1, d = ζ₃²)
```
