`Cbasis(H::HeckeAlgebra)`

returns  a function which gives the  `C`-basis of the Iwahori-Hecke algebra `H`. The algebra `H` should have the functon `rootpara` defined. This basis is  defined as follows (see e.g. [(5.1)Lusztig1985](biblio.htm#Lus85)). Let `W`  be the underlying Coxeter group. For  `x,y ∈ W` let $P_{x,y}$ be the corresponding  Kazhdan–Lusztig polynomial. If $\{T_w ∣ w∈ W\}$ denotes the usual T-basis, then $C_x=\sum_{y\le x}(-1)^{l(x)-l(y)}P_{y,x}(q^{-1})q_x^{1/2}q_y^{-1}  T_y$ for `x  ∈ W`. For example,  we have `Cₛ=qₛ⁻½Tₛ-qₛ½T₁`  for `s ∈  S`. Thus, the transformation matrix between the `T`-basis and the `C`-basis is lower unitriangular, with monomials  in `qₛ` along the diagonal.  In the one-parameter case (all `qₛ` are equal to `v²`) the multiplication rules for the `C` basis are given by:

`Cₛ⋅Cₓ =-(v+v⁻¹)Cₓ`, if `sx<x`, and `Cₛₓ+∑ₜ μ(t,x)Cₜ` if `sx>x`.

where  the sum  is over  all `t`  such that  `t<x`, `l(t)`  and `l(x)` have different parity and `st<t`. The coefficient `μ(t,x)` is the coefficient of degree `(l(x)-l(t)-1)/2` in the Kazhdan–Lusztig polynomial $P_{x,t}$.

The  returned function can take as argument a list of integers (as a vector or  as a list of arguments), representing a Coxeter word, an element of the Coxeter group, or a Hecke element (converted then to the `C'` basis).

```julia-repl
julia> W=coxgroup(:B,3);H=hecke(W,Pol(:v)^2)
hecke(B₃,v²)

julia> T=Tbasis(H);C=Cbasis(H);T(C(1))
-vT.+v⁻¹T₁

julia> C(T(1))
v²C.+vC₁
```

We  can  also  compute  character  values  on  elements in the `C`-basis as follows:

```julia-repl
julia> ref=reflrep(H)
3-element Vector{Matrix{Pol{Int64}}}:
 [-1 0 0; -v² v² 0; 0 0 v²]
 [v² -2 0; 0 -1 0; 0 -v² v²]
 [v² 0 0; 0 v² -1; 0 0 -1]
```

```julia-rep1
julia> c=CharTable(H).irr[charinfo(W).extRefl[[2]],:]
1×10 Matrix{Pol{Int64}}:
 3  2v²-1  v⁸-2v⁴  -3v¹²  2v²-1  v⁴  v⁴-2v²  -v⁶  v⁴-v²  0

julia> hcat(char_values.(C.(classreps(W)),Ref(c))...)
1×10 Matrix{Pol{Int64}}:
 3  -v-v⁻¹  0  0  -v-v⁻¹  2  0  0  1  0
```
