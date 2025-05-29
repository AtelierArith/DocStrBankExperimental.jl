`ClassTypes(G[,p])`

`G`  should be a root  datum or a twisted  root datum representing a finite reductive  group $𝐆 ^F$ and  `p` should be a  prime. The function returns the class types of `G` in characteristic `p` (in good characteristic if `p` is  omitted). Two elements  of $𝐆 ^F$  have the same  class type if their centralizers  are  conjugate.  If  `su`  is  the Jordan decomposition of an element  `x`, the class type of `x` is  determined by the class type of its semisimple part `s` and the unipotent class of `u` in $C_𝐆 (s)$.

The   function  `ClassTypes`  is  presently  only  implemented  for  simply connected  groups, where  $C_𝐆 (s)$  is connected.  This section is a bit experimental and may change in the future.

`ClassTypes`  returns a  `struct` which  contains a  list of classtypes for semisimple  elements,  which  are  represented  by  `subspets`  and contain additionnaly information on the unipotent classes of $C_𝐆 (s)$.

Let us give some examples:

```julia-repl
julia> t=ClassTypes(rootdatum(:sl,3))
ClassTypes(A₂,good characteristic)
┌──────────┬─────────┐
│C_G(s)    │ |C_G(s)|│
├──────────┼─────────┤
│A₂₍₎=Φ₁²  │      Φ₁²│
│A₂₍₎=Φ₁Φ₂ │     Φ₁Φ₂│
│A₂₍₎=Φ₃   │       Φ₃│
│A₂₍₁₎=A₁Φ₁│   qΦ₁²Φ₂│
│A₂        │q³Φ₁²Φ₂Φ₃│
└──────────┴─────────┘
```

By   default,  only  information  about  semisimple  centralizer  types  is returned:   the type, and its generic order.

```julia-rep1
julia> xdisplay(t;unip=true)
ClassTypes(A₂,good characteristic)
┌──────────┬───────────────┐
│C_G(s)    │    u |C_G(su)|│
├──────────┼───────────────┤
│A₂₍₎=Φ₁²  │    1       Φ₁²│
│A₂₍₎=Φ₁Φ₂ │    1      Φ₁Φ₂│
│A₂₍₎=Φ₃   │    1        Φ₃│
│A₂₍₁₎=A₁Φ₁│   11    qΦ₁²Φ₂│
│          │    2       qΦ₁│
│A₂        │  111 q³Φ₁²Φ₂Φ₃│
│          │   21      q³Φ₁│
│          │    3       3q²│
│          │ 3_ζ₃       3q²│
│          │3_ζ₃²       3q²│
└──────────┴───────────────┘
```

Here  we  have  displayed  information  on  unipotent  classes,  with their centralizer.

```julia-rep1
julia> xdisplay(t;nClasses=true)
ClassTypes(A₂,good characteristic)
┌──────────┬─────────────────────────┐
│C_G(s)    │       nClasses  |C_G(s)|│
├──────────┼─────────────────────────┤
│A₂₍₎=Φ₁²  │(q²-5q+2q₃+4)/6       Φ₁²│
│A₂₍₎=Φ₁Φ₂ │       (q²-q)/2      Φ₁Φ₂│
│A₂₍₎=Φ₃   │  (q²+q-q₃+1)/3        Φ₃│
│A₂₍₁₎=A₁Φ₁│       (q-q₃-1)    qΦ₁²Φ₂│
│A₂        │             q₃ q³Φ₁²Φ₂Φ₃│
└──────────┴─────────────────────────┘
```

Here  we have added information on how many semisimple conjugacy classes of `𝐆  ^F` have a given type. The  answer in general involves variables of the form `qₐ` which represent `gcd(q-1,a)`.

Finally an example in bad characteristic:

```julia-rep1
julia> t=ClassTypes(coxgroup(:G,2),2);xdisplay(t;nClasses=true)
ClassTypes(G₂,char. 2)
ClassTypes(G₂,char. 2)
┌──────────┬──────────────────────────────┐
│C_G(s)    │         nClasses     |C_G(s)|│
├──────────┼──────────────────────────────┤
│G₂₍₎=Φ₁²  │(q²-8q+2q₃+10)/12          Φ₁²│
│G₂₍₎=Φ₁Φ₂ │        (q²-2q)/4         Φ₁Φ₂│
│G₂₍₎=Φ₁Φ₂ │        (q²-2q)/4         Φ₁Φ₂│
│G₂₍₎=Φ₆   │    (q²-q-q₃+1)/6           Φ₆│
│G₂₍₎=Φ₃   │    (q²+q-q₃+1)/6           Φ₃│
│G₂₍₎=Φ₂²  │ (q²-4q+2q₃-2)/12          Φ₂²│
│G₂₍₁₎=A₁Φ₁│       (q-q₃-1)/2       qΦ₁²Φ₂│
│G₂₍₁₎=A₁Φ₂│       (q-q₃+1)/2       qΦ₁Φ₂²│
│G₂₍₂₎=Ã₁Φ₁│          (q-2)/2       qΦ₁²Φ₂│
│G₂₍₂₎=Ã₁Φ₂│              q/2       qΦ₁Φ₂²│
│G₂        │                1 q⁶Φ₁²Φ₂²Φ₃Φ₆│
│G₂₍₁₅₎=A₂ │         (q₃-1)/2    q³Φ₁²Φ₂Φ₃│
│G₂₍₁₅₎=²A₂│         (q₃-1)/2    q³Φ₁Φ₂²Φ₆│
└──────────┴──────────────────────────────┘
```

We  notice that if `q` is  a power of `2` such  that `q≡2 (mod 3)`, so that `q₃=1`,  some class types do not exist. We can see what happens by giving a specific value to `q₃`:

```julia-rep1
julia> xdisplay(t(;q_3=1);nClasses=true)
ClassTypes(G₂,char. 2) q₃=1
┌──────────┬──────────────────────────┐
│C_G(s)    │     nClasses     |C_G(s)|│
├──────────┼──────────────────────────┤
│G₂₍₎=Φ₁²  │(q²-8q+12)/12          Φ₁²│
│G₂₍₎=Φ₁Φ₂ │    (q²-2q)/4         Φ₁Φ₂│
│G₂₍₎=Φ₁Φ₂ │    (q²-2q)/4         Φ₁Φ₂│
│G₂₍₎=Φ₆   │     (q²-q)/6           Φ₆│
│G₂₍₎=Φ₃   │     (q²+q)/6           Φ₃│
│G₂₍₎=Φ₂²  │   (q²-4q)/12          Φ₂²│
│G₂₍₁₎=A₁Φ₁│      (q-2)/2       qΦ₁²Φ₂│
│G₂₍₁₎=A₁Φ₂│          q/2       qΦ₁Φ₂²│
│G₂₍₂₎=Ã₁Φ₁│      (q-2)/2       qΦ₁²Φ₂│
│G₂₍₂₎=Ã₁Φ₂│          q/2       qΦ₁Φ₂²│
│G₂        │            1 q⁶Φ₁²Φ₂²Φ₃Φ₆│
└──────────┴──────────────────────────┘
```
