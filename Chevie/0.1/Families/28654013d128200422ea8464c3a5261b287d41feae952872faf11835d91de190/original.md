Families of unipotent characters

The blocks of the (rectangular) matrix $⟨Rᵪ,ρ⟩_{𝐆 ^F}$ when `χ` runs over `Irr(W)`  and  `ρ`  runs  over  the  unipotent  characters,  are called the *Lusztig  families*. When  `𝐆`  is split  and `W`  is a Coxeter group they correspond  on the `Irr(W)` side to two-sided Kazhdan-Lusztig cells –- for split  Spetses they  correspond to  Rouquier blocks  of the  Spetsial Hecke algebra.  The matrix of scalar products  $⟨Rᵪ,ρ⟩_{𝐆 ^F}$ can be completed to   a  square  matrix  $⟨A_{ρ'},ρ⟩_{𝐆  ^F}$  where  $A_{ρ'}$  are  the *characteristic  functions of character  sheaves* on $𝐆  ^F$; this square matrix is called the *Fourier matrix* of the family.

The  'UnipotentCharacters' record in Chevie contains a field '.families', a list of family records containing information on each family, including the Fourier matrix. Here is an example.

```julia-repl
julia> W=coxgroup(:G,2)
G₂

julia> uc=UnipotentCharacters(W);

julia> uc.families
3-element Vector{Family}:
 Family(D(𝔖 ₃),[5, 6, 4, 3, 8, 7, 9, 10],ennola=-5)
 Family(C₁,[1])
 Family(C₁,[2])

julia> uc.families[1]
Family(D(𝔖 ₃),[5, 6, 4, 3, 8, 7, 9, 10],ennola=-5)
Drinfeld double of 𝔖 ₃, Lusztig′s version
┌────────┬────────────────────────────────────────────────────┐
│label   │eigen                                               │
├────────┼────────────────────────────────────────────────────┤
│(1,1)   │    1 1//6  1//2  1//3  1//3  1//6  1//2  1//3  1//3│
│(g₂,1)  │    1 1//2  1//2     .     . -1//2 -1//2     .     .│
│(g₃,1)  │    1 1//3     .  2//3 -1//3  1//3     . -1//3 -1//3│
│(1,ρ)   │    1 1//3     . -1//3  2//3  1//3     . -1//3 -1//3│
│(1,ε)   │    1 1//6 -1//2  1//3  1//3  1//6 -1//2  1//3  1//3│
│(g₂,ε)  │   -1 1//2 -1//2     .     . -1//2  1//2     .     .│
│(g₃,ζ₃) │   ζ₃ 1//3     . -1//3 -1//3  1//3     .  2//3 -1//3│
│(g₃,ζ₃²)│  ζ₃² 1//3     . -1//3 -1//3  1//3     . -1//3  2//3│
└────────┴────────────────────────────────────────────────────┘

julia> charnames(uc)[uc.families[1].charNumbers]
8-element Vector{String}:
 "phi2,1"
 "phi2,2"
 "phi1,3''"
 "phi1,3'"
 "G2[1]"
 "G2[-1]"
 "G2[E3]"
 "G2[E3^2]"
```

The  Fourier matrix is obtained  by 'fourier(f)'; the field 'f.charNumbers' holds  the indices of the unipotent characters  which are in the family. We obtain  the list of eigenvalues of Frobenius for these unipotent characters by  'Eigenvalues(f)'. The Fourier matrix  and vector of eigenvalues satisfy the  properties of  *fusion data*,  see below.  The field 'f.charLabels' is what  is displayed  in the  column 'labels'  when displaying the family. It contains  labels naturally attached to lines  of the Fourier matrix. In the case   of  reductive  groups,   the  family  is   always  attached  to  the "drinfeld_double"  of a small finite group  and the '.charLabels' come from this construction.
