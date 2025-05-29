`ennola(W[,z=E(gcd(degrees(W)))])`

Let  `W` be an irreducible spetsial reflection  group or coset, and `z` the generator of the center of `W`, viewed as the root of unity `E(gcd(degrees(W)))])`.  Let `𝔾` be  the spets attached  to `W`. A property checked  case-by case is  that, for a  unipotent character `γ`  of `𝔾` with polynomial generic degree `deg γ(q)` , `deg γ(zq)` is equal to `±deg γ'(q)` for  another unipotent character `γ'`; `±γ'` is called the Ennola transform of `γ`. For `W` a Weyl group, the spets `𝔾` is a finite reductive group, in which  case `z=-1`  if `-1`  is in  `W` and  `z=1` otherwise.  The function returns  the  signed  permutation  `e`  done  by  `ennola` on the unipotent degrees (as an `SPerm` of `1:length(UnipotentCharacters(W))`).

The `SPerm` `e` is not uniquely determined by the degrees since two degrees may  be equal, but is uniquely determined by some additional axioms that we do not recall here (they include a description of the Ennola-permutation in terms of the Z-based rings attached to each Lusztig family).

If  a second argument `z` is given, it should be a power of the default `z` and the corresponding power of `e` is returned.

```julia-repl
julia> ennola(rootdatum("3D4"))
SPerm{Int64}: (3,-4)(5,-5)(6,-6)(7,-8)

julia> ennola(complex_reflection_group(14))
SPerm{Int64}: (2,43,-14,16,41,34)(3,35,40,18,-11,42)(4,-37,25,-17,-26,-36)(5,-6,-79)(7,-7)(8,-74)(9,-73)(10,-52,13,31,-50,29)(12,53,15,32,-51,-30)(19,71,70,21,67,68,20,69,72)(22,-39,27,-33,-28,-38)(23,24,-66,-23,-24,66)(44,46,49,-44,-46,-49)(45,48,47,-45,-48,-47)(54,-63,-55,-57,62,-56)(58,-65,-59,-61,64,-60)(75,-77)(76,-76)(78,-78)

```

The  above example shows  that it may  happen that the  order of `z`-Ennola (here 18) is greater than the order of `z` (here 6); this is related to the presence  of irrationalities  `q⅓` in  the character  table of the spetsial Hecke algebra of `W`.

For a non-irreducible group, `z`-ennola is defined if `z` can be considered an element of the the centre of each irreducible component.
