`Category(atomsfrom::Function,o;action::Function=^)`

constructs   a  category  from  an  initial   object  `o`  and  a  function `atomsfrom(o)`  which given object `o` returns atoms from `o` as "maps" `m` such that the target object is `action(o,m)`.

As an example we construct a Garside category associated to the braid group of  `G₃₁`, realized as the  centralizer of a 4th  root of `δ³⁰` in the dual braid  monoid of `E₈`; that is the fixed points of `δad¹⁵` in the 2-divided category.

```julia-repl
julia> W=coxgroup(:E,8);M=DualBraidMonoid(W)
DualBraidMonoid(E₈,c=[1, 4, 6, 8, 3, 2, 5, 7])

julia> s4=left_divisors(M,M.δ,4); # simples of length 4

julia> s=M(s4[findfirst(x->x*δad(M,x,8)==M.δ,s4)])#an object of 2-divided cat
(1 8 17 35)

julia> "the right-lcms of the `δⁱ`-orbits on `leftdescents(b)`"
       function satoms(b,i)
         M=b.M
         ld=M.atoms[leftdescents(b)]
         di=Perm(ld,δad.(Ref(M),ld,i))
         if isnothing(di) error(b," is not δ^$i-stable") end
         map(o->M(rightlcm(M,ld[o]...)),orbits(di,eachindex(ld)))
       end
satoms

julia> Category(x->satoms(x,15),s;action=(o,m)->inv(m)*o*δad(m,8))
category with 88 objects and 660 generating maps
```
