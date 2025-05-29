`drinfeld_double(g;lu=false,pivotal=nothing)`

Given  a (usually small) finite group  `Γ`, Lusztig has associated a family (a  Fourier matrix, a list of eigenvalues of Frobenius) which describes the representation ring of the Drinfeld double of the group algebra of `Γ`, and for   some  appropriate  small  groups  describes  a  family  of  unipotent characters. We do not explain the details of this construction, but explain how its final result building Lusztig's Fourier matrix, and a variant of it that we use in Spetses, from `Γ`.

The  elements of the family are in bijection  with the set `𝓜 (Γ)` of pairs `(x,φ)`  taken up to  `Γ`-conjugacy, where `x∈Γ`  and `φ` is an irreducible complex-valued   character  of  `C_Γ(x)`.  To  such  a  pair  `ρ=(x,φ)`  is associated  an  eigenvalue  of  Frobenius  defined  by  $ω_ρ:=φ(x)/φ(1)$. Lusztig  then defines a Fourier matrix `S₀` whose coefficient is given, for `ρ=(x,φ)` and `ρ'=(x', φ')`, by:

$S₀_{ρ,ρ'}:=|C_Γ(x)⁻¹|∑_{ρ₁=(x₁,φ₁)}φ₁(x)φ(y₁)$

where  the sum is over all pairs `ρ₁∈𝓜 (Γ)` which are `Γ`-conjugate to `ρ'` and  such that $y₁∈ C_Γ(x)$. This  coefficient also represents the scalar product $⟨ρ,ρ'⟩_{𝐆^F}$ of the corresponding unipotent characters.

A  way to  understand the  formula for  $S₀_{ρ,ρ'}$ better is to consider another  basis of the complex  vector space with basis  `𝓜 (Γ)`, indexed by the  pairs  `(x,y)`  taken  up  to  `Γ`-conjugacy,  where  `x`  and `y` are commuting  elements  of  `Γ`.  This  basis  is  called  the basis of Mellin transforms, and given by:

$(x,y)=∑_{φ∈ Irr(C_Γ(x))}φ(y)(x,φ)$

In  the  basis  of  Mellin  transforms,  the  linear  map  `S₀` is given by `(x,y)↦(x⁻¹,y⁻¹)`  and  the  linear  transformation  `T` which sends `ρ` to `ω_ρρ`   becomes  `(x,y)↦(x,xy)`.   These  are   particular  cases  of  the permutation  representation of `GL₂(ℤ)`  on the basis  of Mellin transforms where $\begin{pmatrix}a&b\cr c&d\end{pmatrix}$ acts by `(x,y)↦(xᵃyᵇ,xᶜyᵈ)`.

Fourier  matrices in finite reductive groups  are given by the above matrix `S₀`.  But for non-rational Spetses, we use a different matrix `S` which in the  basis of Mellin transforms  is given by `(x,y)↦(y⁻¹,x)`. Equivalently, the formula $S_{ρ,ρ'}$ differs from the formula for $S₀_{ρ,ρ'}$ in that there  is no complex conjugation  of `χ₁`; thus the  matrix `S` is equal to `S₀` multiplied on the right by the permutation matrix which corresponds to `(x,φ)↦(x,φ)`.  The advantage of the matrix `S`  over `S₀` is that the pair `S,T`  satisfies directly the axioms for  fusion data (see below); also the matrix `S` is symmetric, while `S₀` is Hermitian.

Thus there are two variants of 'drinfeld_double`:

`drinfeld_double(g;lu=false)`

returns  a family  containing Lusztig's  Fourier matrix  `S₀`, and an extra field  '.perm'  containing  the  permutation  of  the  indices  induced  by `(x,φ)↦(x,φ)`,  which allows  to recover  `S`, as  well as  an extra field `:lusztig', set to 'true'.

`drinfeld_double(g)`

returns a family with the matrix `S`, which does not have fields '.lusztig' or '.perm'.

The family record 'f' returned also has the fields:

`:group`: the group `Γ`.

`:charLabels`: a list of labels describing the pairs `(x,φ)`, and thus also specifying in which order they are taken.

`:fourierMat`: the Fourier matrix (the matrix `S` or `S₀` depending on the call).

`:eigenvalues`: the eigenvalues of Frobenius.

`:xy`: a list of pairs '[x,y]' which are representatives of the `Γ`-orbits of pairs of commuting elements.

`:mellinLabels`: a list of labels describing the pairs '[x,y]'.

`:mellin`:  the base change matrix between  the basis `(x,φ)` and the basis of   Mellin  transforms,   so  that   |f.fourierMat^(f.mellin^-1)|  is  the permutation  matrix (for `(x,y)↦(y⁻¹,x)`  or `(x,y)↦(y⁻¹,x⁻¹)` depending on the call).

`:special`: the index of the special element, which is `(x,φ)=(1,1)`.

```julia-rep1
julia> drinfeld_double(coxsym(3)) # needs "using GAP"
Family(drinfeld_double(coxsym(3)),8)
Drinfeld double D(coxsym(3))
┌───────┬────────────────────────────────────────────────────┐
│label  │eigen                                               │
├───────┼────────────────────────────────────────────────────┤
│(1,1)  │    1  1//6  1//3 1//6 -1//2 -1//2  1//3  1//3  1//3│
│(1,X.2)│    1  1//3  2//3 1//3     .     . -1//3 -1//3 -1//3│
│(1,X.3)│    1  1//6  1//3 1//6  1//2  1//2  1//3  1//3  1//3│
│(21,1) │    1 -1//2     . 1//2  1//2 -1//2     .     .     .│
│(21,-1)│   -1 -1//2     . 1//2 -1//2  1//2     .     .     .│
│(3,1)  │    1  1//3 -1//3 1//3     .     .  2//3 -1//3 -1//3│
│(3,ζ₃) │   ζ₃  1//3 -1//3 1//3     .     . -1//3 -1//3  2//3│
│(3,ζ₃²)│  ζ₃²  1//3 -1//3 1//3     .     . -1//3  2//3 -1//3│
└───────┴────────────────────────────────────────────────────┘

julia> drinfeld_double(coxsym(3);lu=true)
Family(Ldrinfeld_double(coxsym(3)),8)
Lusztig′sDrinfeld double D(coxsym(3))
┌───────┬────────────────────────────────────────────────────┐
│label  │eigen                                               │
├───────┼────────────────────────────────────────────────────┤
│(1,1)  │    1  1//6  1//3 1//6 -1//2 -1//2  1//3  1//3  1//3│
│(1,X.2)│    1  1//3  2//3 1//3     .     . -1//3 -1//3 -1//3│
│(1,X.3)│    1  1//6  1//3 1//6  1//2  1//2  1//3  1//3  1//3│
│(21,1) │    1 -1//2     . 1//2  1//2 -1//2     .     .     .│
│(21,-1)│   -1 -1//2     . 1//2 -1//2  1//2     .     .     .│
│(3,1)  │    1  1//3 -1//3 1//3     .     .  2//3 -1//3 -1//3│
│(3,ζ₃) │   ζ₃  1//3 -1//3 1//3     .     . -1//3  2//3 -1//3│
│(3,ζ₃²)│  ζ₃²  1//3 -1//3 1//3     .     . -1//3 -1//3  2//3│
└───────┴────────────────────────────────────────────────────┘
```

The  keyword `pivotal`  describes the  pivotal structure  as a tuple of the pivotal  element and the vector  of values of the  pivotal character on the generators of `g`.
