# Algebraic groups and semi-simple elements

Let  us fix an  algebraically closed field  `K` and let  `𝐆` be a connected reductive  algebraic group over `K`. Let `𝐓` be a maximal torus of `𝐆`, let `X(𝐓)`  be the  character group  of `𝐓`  (resp. `Y(𝐓)`  the dual lattice of one-parameter  subgroups  of  `𝐓`)  and  `Φ`  (resp  `Φ^`) the roots (resp. coroots) of `𝐆` with respect to `𝐓`.

Then  `𝐆` is  determined up  to isomorphism  by the  *root datum* `(X(𝐓),Φ, Y(𝐓),Φ^)`.  In algebraic terms, this consists  in giving a free `ℤ`-lattice `X=X(𝐓)` of dimension the *rank* of `𝐓` (which is also called the *rank* of `𝐆`),  and a root system `Φ ⊂ X`,  and similarly giving the dual roots `Φ^⊂ Y=Y(𝐓)`.

This  is obtained  by a  slight generalisation  of our  setup for a Coxeter group `W`. This time we assume that the canonical basis of the vector space `V`  on which `W`  acts is a  `ℤ`-basis of `X`,  and `Φ` is  specified by a matrix  `simpleroots(W)` whose rows are the  simple roots expressed in this basis  of `X`. Similarly  `Φ^` is described  by a matrix `simplecoroots(W)` whose  rows are the simple  coroots in the basis  of `Y` dual to the chosen basis of `X`. The duality pairing between `X` and `Y` is the canonical one, that  is  the  pairing  between  vectors  `x∈  X`  and  `y∈  Y` is given by `transpose(x)*y`. Thus, we must have the relation `simplecoroots(W)*permutedims(simpleroots(W))=cartan(W)`.

We  get this by using the function `rootdatum`, whose arguments are the two matrices `simpleroots(W)` and `simplecoroots(W)` described above. The roots need not generate `V`, so the matrices need not be square. For example, the root datum of the linear group of rank 3 can be obtained as:

```julia-repl
julia> W=rootdatum([-1 1 0;0 -1 1],[-1 1 0;0 -1 1])
A₂Φ₁

julia> reflrep(W,W(1))
3×3 Matrix{Int64}:
 0  1  0
 1  0  0
 0  0  1
```

here  the  Weyl  group  is  the  symmetric  group  on  3  letters acting by permutation of the basis of `X`. The dimension of `X`, `size(simpleroots(W),2)`,  is the *rank* and  the dimension of the subspace generated   by   the   roots,   `size(simpleroots(W),1)`,   is  called  the *semi-simple rank*. In the example the rank is 3 and the semisimple rank is

2. 

The  default form  `W=coxgroup(:A,2)` defines  the adjoint  algebraic group (the group in its isogeny class with a trivial centre). In this case `Φ` is a   basis  of  `X`,   so  `simpleroots(W)`  is   the  identity  matrix  and `simplecoroots(W)` is the Cartan matrix `cartan(W)` of the root system.

The   form  `coxgroup(:A,2,sc=true)`   constructs  the   semisimple  simply connected  algebraic  group,  where  `simpleroots(W)`  is the transposed of `cartan(W)` and `simplecoroots(W)` is the identity matrix.

An  extreme form of root data can  be specified more conveniently: when `W` is  the trivial `coxgroup()` (in this case `𝐆` is a torus), the root datum has  no roots, thus  is entirely determined  by the rank  `r`. The function `torus(r)`  constructs  such  a  root  datum  (it could be also obtained by giving two `0×r` matrices to `rootdatum`).

Finally,  the `rootdatum` function also understands some familiar names for the  algebraic groups for which it gives the results that could be obtained by giving the appropriate `simpleroots(W)` and `simplecoroots(W)` matrices:

```julia-repl
julia> rootdatum(:gl,3)   # same as the previous example
gl₃
```

The types of root data which are understood are  `:gl, :pgl, :sl, :slmod, :tgl :sp, :csp, :psp, :so, :pso, :cso, :halfspin,    :gpin, :spin, :E6, :E6sc, :CE6, :E7, :E7sc, :CE7, :E8, :F4, :G2`.

## Semisimple elements

We  construct semi-simple elements in two ways. The first way is for finite order  elements of `𝐓`, which over an algebraically closed field `K` are in bijection  with elements  of `Y⊗  ℚ /ℤ`  whose denominator  is prime to the characteristic of `K`. These are represented as a vector of `Rational`s `r` such  that `0≤r<1`. The function `ss`  constructs such a semisimple element from a vector of `Rational`s.

More generally a torus `𝐓` over a field `K` is isomorphic to `(Kˣ)^n` where `n`  is the dimension  of `𝐓`, so  a vector of  elements of `Kˣ`  is a more general representation which is produced by the function `SemisimpleElement`;  in  this  setting  the  result  of  `ss` is naturally interpreted  as a  `Vector{Root1}`, so  it can  also be obtained by calling `SemisimpleElement` which such a vector.

```julia-repl
julia> G=rootdatum(:sl,4)
sl₄

julia> ss(G,[1//3,1//4,3//4,2//3])
SemisimpleElement{Root1}: <ζ₃,ζ₄,ζ₄³,ζ₃²>

julia> SemisimpleElement(G,[E(3),E(4),E(4,3),E(3,2)])
SemisimpleElement{Root1}: <ζ₃,ζ₄,ζ₄³,ζ₃²>

julia> L=reflection_subgroup(G,[1,3])
A₃₍₁₃₎=A₁×A₁Φ₁

julia> C=algebraic_center(L)
(Z0 = SubTorus(A₃₍₁₃₎=A₁×A₁Φ₁,[1 2 1]), AZ = Group(SemisimpleElement{Root1}[<1,1,-1>]), descAZ = [[1, 2]], ZD = Group(SemisimpleElement{Root1}[<-1,1,1>, <1,1,-1>]))

julia> T=torsion_subgroup(C.Z0,3)
Group(SemisimpleElement{Root1}[<ζ₃,ζ₃²,ζ₃>])

julia> e=sort(elements(T))
3-element Vector{SemisimpleElement{Root1}}:
 <1,1,1>
 <ζ₃,ζ₃²,ζ₃>
 <ζ₃²,ζ₃,ζ₃²>
```

In  the above, the Levi subgroup  `L` of `SL₄` consisting of block-diagonal matrices  of shape  `2×2` is  constructed. The  function `algebraic_center` returns  a named tuple with : the  neutral component `Z⁰` of the center `Z` of `L`, represented by a basis of `Y(Z⁰)`, a complement subtorus `S` of `𝐓` to  `Z⁰`  represented  similarly  by  a  basis  of  `Y(S)`, and semi-simple elements  representing the classes of `Z` modulo  `Z⁰` , chosen in `S`. The classes  `Z/Z⁰` also biject to the fundamental  group as given by the field `.descAZ`,  see [`algebraic_center`](@ref) for  an explanation. Finally the semi-simple elements of order 3 in `Z⁰` are computed.

```julia-repl
julia> e[3]^G(2)
SemisimpleElement{Root1}: <ζ₃²,1,ζ₃²>

julia> orbit(G,e[3])
6-element Vector{SemisimpleElement{Root1}}:
 <ζ₃²,ζ₃,ζ₃²>
 <ζ₃²,1,ζ₃²>
 <ζ₃,1,ζ₃²>
 <ζ₃²,1,ζ₃>
 <ζ₃,1,ζ₃>
 <ζ₃,ζ₃²,ζ₃>
```

Here  is the same  computation as above  performed with semisimple elements whose  coefficients are in the  finite field `FF(4)`, representing elements of `sl₄(𝔽₄)`.

```julia-repl
julia> G=rootdatum(:sl,4)
sl₄

julia> s=SemisimpleElement(G,Z(4).^[1,2,1])
SemisimpleElement{FFE{2}}: <Z₄,Z₄²,Z₄>

julia> s^G(2)
SemisimpleElement{FFE{2}}: <Z₄,1,Z₄>

julia> orbit(G,s)
6-element Vector{SemisimpleElement{FFE{2}}}:
 <Z₄,Z₄²,Z₄>
 <Z₄,1,Z₄>
 <Z₄²,1,Z₄>
 <Z₄,1,Z₄²>
 <Z₄²,1,Z₄²>
 <Z₄²,Z₄,Z₄²>
```

We can compute the centralizer $C_𝐆 (s)$ of a semisimple element in `𝐆`:

```julia-repl
julia> G=coxgroup(:A,3)
A₃

julia> s=ss(G,[0,1//2,0])
SemisimpleElement{Root1}: <1,-1,1>

julia> centralizer(G,s)
A₃₍₁₃₎=(A₁A₁)Φ₂
```

The  result is an  `ExtendedReflectionGroup`; the reflection  group part is the Weyl group of $C_𝐆 ⁰(s)$ and the extended part are representatives of $C_𝐆  (s)$  modulo  $C_𝐆⁰(s)$  taken  as  diagram  automorphisms of the reflection  part.  Here  it  is  printed  as  a  coset  $C_𝐆 ⁰(s)ϕ$ which generates $C_𝐆 (s)$.
