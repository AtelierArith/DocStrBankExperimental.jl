`UnipotentClasses(W[,p])`

`W` should be a `FiniteCoxeterGroup` record for a Weyl group or `rootdatum` describing  a reductive algebraic group `𝐆`.  The function returns a record containing information about the unipotent classes of `𝐆` in characteristic `p`  (if omitted, `p`  is assumed to  be any good  characteristic for `𝐆`). This contains the following fields:

`group`: a pointer to `W`

`p`: the characteristic of the field for which the unipotent classes were computed. It is `0` for any good characteristic.

`orderclasses`:  a list describing the Hasse diagram of the partial order induced   on   unipotent   classes   by   the  closure  relation.  That  is `.orderclasses[i]`  is the list of `j` such that $C̄ⱼ⊋ C̄ᵢ$  and  there  is no  class  $Cₖ$  such  that $C̄ⱼ⊋ C̄ₖ⊋ C̄ᵢ$.

`classes`:  a list of records holding information for each unipotent class. See  the  help  for  [`UnipotentClass`](@ref)  for  a  description of these records.

`springerseries`:  a list of records, each  of which describes a Springer series  of `𝐆`.

The  records  describing  individual  Springer  series  have  the following fields:

`levi`:the  indices of the  reflections corresponding to  the Levi subgroup `𝐋`  where  lives  the  cuspidal  local  system `ι` from which the Springer series is induced.

`relgroup`: The relative Weyl group $N_𝐆(𝐋,ι)/𝐋$. The first series is the principal series for which `.levi=[]` and `.relgroup=W`.

`locsys`:  a  list  of  length  `nconjugacy_classes(.relgroup)`, holding in `i`-th  position a  pair describing  which local  system corresponds to the `i`-th  character of  $N_𝐆(𝐋,ι)$. The  first element  of the  pair is the index  of the concerned unipotent class `u`, and the second is the index of the corresponding character of `A(u)`.

`Z`:  the central character associated  to the Springer series, specified by its value on the generators of the center.

```julia-repl
julia> W=rootdatum(:sl,4)
sl₄

julia> uc=UnipotentClasses(W);

julia> uc.classes
5-element Vector{UnipotentClass}:
 UnipotentClass(1111)
 UnipotentClass(211)
 UnipotentClass(22)
 UnipotentClass(31)
 UnipotentClass(4)
```

The  `show`  function  for  unipotent  classes  accepts  all the options of `showtable`  and  of  `charnames`.  Giving  the  option  `mizuno`  (resp. `shoji`)  uses  the  names  given  by  Mizuno  (resp.  Shoji) for unipotent classes.  Moreover,  there  is  also  an  option  `fourier` which gives the Springer  correspondence tensored with the  sign character of each relative Weyl  group,  which  is  the  correspondence obtained via a Fourier-Deligne transform  (here  we  assume  that  `p`  is  very  good, so that there is a nondegenerate  invariant bilinear form on the Lie algebra, and also one can identify nilpotent orbits with unipotent classes).

Here is how to display the non-cuspidal part of the Springer correspondence of  the unipotent  classes of  `E₆` using  the notations  of Mizuno for the classes  and those  of Frame  for the  characters of  the Weyl group and of Spaltenstein  for the characters  of `G₂` (this  is convenient for checking our data with the original paper of Spaltenstein):

```julia-rep1
julia> uc=UnipotentClasses(rootdatum(:E6sc));

julia> xdisplay(uc;cols=[5,6,7],spaltenstein=true,frame=true,mizuno=true,
      order=false)
┌──────┬─────────────────────────────────────────────────────┐
│u     │             E₆(Φ₁⁶) G₂(A₂×A₂Φ₁²)/ζ₃ G₂(A₂×A₂Φ₁²)/ζ₃²│
├──────┼─────────────────────────────────────────────────────┤
│E₆    │                1:1ₚ            ζ₃:1            ζ₃²:1│
│E₆(a₁)│                1:6ₚ           ζ₃:εₗ           ζ₃²:εₗ│
│D₅    │              Id:20ₚ                                 │
│A₅+A₁ │        -1:15ₚ 1:30ₚ           ζ₃:θ′           ζ₃²:θ′│
│A₅    │              1:15_q           ζ₃:θ″           ζ₃²:θ″│
│D₅(a₁)│              Id:64ₚ                                 │
│A₄+A₁ │              Id:60ₚ                                 │
│D₄    │              Id:24ₚ                                 │
│A₄    │              Id:81ₚ                                 │
│D₄(a₁)│111:20ₛ 3:80ₛ 21:90ₛ                                 │
│A₃+A₁ │              Id:60ₛ                                 │
│2A₂+A₁│               1:10ₛ          ζ₃:ε_c          ζ₃²:ε_c│
│A₃    │             Id:81ₚ′                                 │
│A₂+2A₁│             Id:60ₚ′                                 │
│2A₂   │              1:24ₚ′            ζ₃:ε            ζ₃²:ε│
│A₂+A₁ │             Id:64ₚ′                                 │
│A₂    │      11:15ₚ′ 2:30ₚ′                                 │
│3A₁   │            Id:15_q′                                 │
│2A₁   │             Id:20ₚ′                                 │
│A₁    │              Id:6ₚ′                                 │
│1     │              Id:1ₚ′                                 │
└──────┴─────────────────────────────────────────────────────┘
```
