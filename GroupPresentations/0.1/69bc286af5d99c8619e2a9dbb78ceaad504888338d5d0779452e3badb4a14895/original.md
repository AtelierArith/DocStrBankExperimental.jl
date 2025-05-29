`simplify(G)`

`simplify`  applies  Tietze  transformations  to a  copy of  the presentation of the given finitely presented group `G` in order to reduce it with respect to  the number of generators, the number of relators, and the relator lengths.

`simplify` returns the resulting finitely presented group (which is isomorphic to `G`).

```julia-repl
julia> @AbsWord a,b,c,d,e,f

julia> F=FpGroup([a,b,c,d,e,f])
FreeGroup(a,b,c,d,e,f)

julia> G=F/[a^2,b^2,d*f^-1,e^2,f^2,a*b^-1*c,a*e*c^-1,b*d^-1*c,c*d*e^-1,a*f*c^-2,c^4]
FreeGroup(a,b,c,d,e,f)/[a²,b²,df⁻¹,e²,f²,ab⁻¹c,aec⁻¹,bd⁻¹c,cde⁻¹,afc⁻²,c⁴]

julia> simplify(G)
FreeGroup(a,c)/[a²,ac⁻¹ac⁻¹,c⁴]
```

In fact, the call

```julia-rep1
julia> simplify(G)
```

is an abbreviation of the call sequence

```julia-rep1
julia> P=Presentation(G,0);simplify(P);FpGroup(P)
```

which applies  a rather simple-minded strategy of  Tietze transformations to the intermediate presentation `P`. If for  some  concrete group the resulting presentation  is unsatisfying, then  you  should  try  a  more  sophisticated,  interactive  use of  the available Tietze transformation functions  (see "Tietze Transformations").
