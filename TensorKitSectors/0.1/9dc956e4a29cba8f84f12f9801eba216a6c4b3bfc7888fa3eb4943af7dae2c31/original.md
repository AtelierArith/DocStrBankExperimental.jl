```
BraidingStyle(::Sector) -> ::BraidingStyle
BraidingStyle(I::Type{<:Sector}) -> ::BraidingStyle
```

Return the type of braiding and twist behavior of sectors of type `I`, which can be either

  * `Bosonic()`: symmetric braiding with trivial twist (i.e. identity)
  * `Fermionic()`: symmetric braiding with non-trivial twist (squares to identity)
  * `Anyonic()`: general $R_(a,b)^c$ phase or matrix (depending on `SimpleFusion` or   `GenericFusion` fusion) and arbitrary twists

Note that `Bosonic` and `Fermionic` are subtypes of `SymmetricBraiding`, which means that braids are in fact equivalent to crossings (i.e. braiding twice is an identity: `isone(Rsymbol(b,a,c)*Rsymbol(a,b,c)) == true`) and permutations are uniquely defined.
