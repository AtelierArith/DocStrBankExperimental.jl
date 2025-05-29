This  module contains  functions for  computing with  unipotent elements of reductive  groups; specifically to  compute with elements  of the unipotent radical of a Borel subgroup of a connected algebraic reductive group; these functions  were initially written by Olivier Dudas in GAP3, partly inspired by older C code of Jean Michel.

The  unipotent radical of a  Borel subgroup is the  product in any order of the root subgroups associated to the positive roots. We fix an order, which gives a canonical form to display elements and to compare them.

The  computations use the Steinberg relations between root subgroups, which come from the choice of a Chevalley basis of the Lie algebra. The reference we  follow is [Carter1972,  chapters 4 to  6](biblio.htm#Car72b), but it is possible  to use another  choice of Chevalley  basis, see the documentation for `UnipotentGroup`.

We  start with  a root  datum specified  by a  Weyl group  `W` and  build a `struct  UnipotentGroup`  which  contains  information  about  the  maximal unipotent  subgroup  of  the  corresponding  reductive  group,  that is the unipotent radical of the Borel subgroup determined by the positive roots.

```julia-repl
julia> W=coxgroup(:E,6)
E₆

julia> U=UnipotentGroup(W)
UnipotentGroup(E₆)
```

Now, if `α=roots(W,2)`, we construct the element `u_α(4)` of the root subgroup `u_α`:

```julia-repl
julia> U(2=>4)
u2(4)
```

If we do not specify the coefficient we make by default `u_α(1)`, so we have also:

```julia-repl
julia> U(2)^4
u2(4)
```

We can make more complicated elements:

```julia-repl
julia> U(2=>4)*U(4=>5)
u2(4)u4(5)

julia> U(2=>4,4=>5)
u2(4)u4(5)
```

If the roots are not in order the element is normalized:

```julia-repl
julia> U(4=>5,2=>4)
u2(4)u4(5)u8(-20)
```

It is possible to display the decomposition of the roots in simple roots instead of their index:

```julia-rep1
julia> xdisplay(U(4=>5,2=>4);root=true)
u₀₁₀₀₀₀(4)u₀₀₀₁₀₀(5)u₀₁₀₁₀₀(-20)
```

The coefficients in the root subgroups can be elements of arbitrary rings. Here is an example using `Mvp`'s:

```julia-repl
julia> W=coxgroup(:E,8);U=UnipotentGroup(W)
UnipotentGroup(E₈)

julia> u=U(map(i->i=>Z(2)*Mvp(Symbol("x",Char(i+0x2080))),1:8)...)
u1(x₁)u2(x₂)u3(x₃)u4(x₄)u5(x₅)u6(x₆)u7(x₇)u8(x₈)
```

```julia-rep1
julia> cut(xrepr(u^16;limit=true,root=true),before="u",width=60)
u₂₂₃₄₃₂₁₀(x₁²x₂²x₃³x₄⁴x₅³x₆²x₇)
u₁₂₃₄₃₂₁₁(x₁x₂²x₃³x₄⁴x₅³x₆²x₇x₈)
u₁₂₂₄₃₂₂₁(x₁x₂²x₃²x₄⁴x₅³x₆²x₇²x₈)
u₁₂₂₃₃₃₂₁(x₁x₂²x₃²x₄³x₅³x₆³x₇²x₈)
u₂₂₃₄₃₂₁₁(x₁²x₂²x₃³x₄⁴x₅³x₆²x₇x₈)
u₁₂₂₄₃₃₂₁(x₁x₂²x₃²x₄⁴x₅³x₆³x₇²x₈)
u₁₂₂₄₄₃₂₁(x₁x₂²x₃²x₄⁴x₅⁴x₆³x₇²x₈)
u₂₂₃₄₃₃₂₁(x₁²x₂²x₃³x₄⁴x₅³x₆³x₇²x₈)
u₁₂₃₄₄₃₂₁(x₁x₂²x₃³x₄⁴x₅⁴x₆³x₇²x₈)
u₂₂₃₄₄₃₂₁(x₁²x₂²x₃³x₄⁴x₅⁴x₆³x₇²x₈)
u₂₃₃₅₄₃₂₁(x₁²x₂³x₃³x₄⁵x₅⁴x₆³x₇²x₈)
u₂₂₄₅₄₃₂₁(x₁²x₂²x₃⁴x₄⁵x₅⁴x₆³x₇²x₈)
u₂₃₄₆₅₄₃₂(x₁²x₂³x₃⁴x₄⁶x₅⁵x₆⁴x₇³x₈²)
```

```julia-repl
julia> u^32
()
```

The  above computation shows  that in characteristic  2 the exponent of the unipotent  group of `E₈` is 32. More precisely, squaring doubles the height of  the involved roots, so in the above `u¹⁶` involves only roots of height 16 or more.

Various  actions are  defined on  unipotent elements.  Elements of the Weyl group  act (through certain representatives) as long as no root subgroup is in their inversion set:

```julia-repl
julia> W=coxgroup(:G,2)
G₂

julia> U=UnipotentGroup(W);@Mvp x,y

julia> u=U(1=>x,3=>y)
u1(x)u3(y)

julia> u^W(2,1)
u4(y)u5(x)
```

```julia-repl
julia> u^W(1)
ERROR: u1(x)u3(y) should have no coefficient on root 1
```

Semisimple elements act by conjugation:

```julia-repl
julia> s=SemisimpleElement(W,[E(3),2])
SemisimpleElement{Cyc{Int64}}: <ζ₃,2>

julia> u^s
u1(ζ₃x)u3(2ζ₃y)
```

As well as unipotent elements:

```julia-repl
julia> u^U(2)
u1(x)u3(x+y)u4(-x-2y)u5(x+3y)u6(x²+3xy+3y²)
```
