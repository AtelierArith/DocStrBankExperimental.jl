`Coset(G::Group,phi=one(G))`  constructs the (left)  coset `G.phi` where `G isa  Group{<:T}` and `phi isa  T`, as an object  of type `Cosetof{T}`. This general  coset knows only the general methods for a coset `C=G.phi` defined in this module, which are

  * `Group(C)` returns `G`.
  * `isone(C)` returns `true` iff `phi in G`
  * `one(C)` returns the trivial coset `G.1`
  * `length(C)` returns `length(G)`
  * `elements(C)` returns `elements(G).*Ref(phi)`
  * `x in C` returns `x/phi in G`
