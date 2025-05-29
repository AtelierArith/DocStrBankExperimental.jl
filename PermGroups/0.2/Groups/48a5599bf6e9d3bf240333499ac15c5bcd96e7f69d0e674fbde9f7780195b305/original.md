`NormalCoset(G::Group,phi=one(G))`  constructs the coset `C=G.phi` where `G isa  Group{<:T}` and `phi isa T`,  as an object of type `NormalCosetof{T}`. It  is assumed that `phi` normalizes `G`. This general coset knows only the general  methods defined for normal cosets in the module `Groups`, which in addition to those defined for cosets (see `Coset`) are

  * `inv(C)` return `G.inv(phi)` (assumed equal to `inv(phi).G`)
  * `C*D` given another coset `G.psi` returns `G.phi*psi`
  * `C/D` given another coset `G.psi` returns `G.phi*inv(psi)`
  * `C^D` given another coset `G.psi` returns `G.inv(psi)*phi*psi`
  * `C^n` returns `G.phi^n`
  * `order(C)` the smallest `n` such that `isone(C^n)`

The  conjugacy  classes  of  a  normal  coset  `G.phi`  are relative to the conjugation action of `G` on `G.phi`. We have the functions `conjugacy_classes, nconjugacy_classes, classreps, position_class`.

Finally  the function  `G/H` for  two groups  constructs the  quotient as a group of `NormalCoset`s, and `fusion_conjugacy_classes(H::NormalCoset,G::NormalCoset)`   expresses   the fusion of conjugacy classes.
