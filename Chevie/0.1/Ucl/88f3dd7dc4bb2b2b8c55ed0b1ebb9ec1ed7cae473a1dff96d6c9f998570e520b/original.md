A `struct UnipotentClass` representing the class `C` of a unipotent element `u`  of the reductive  group `𝐆` with  Weyl group `W`,  contains always the following information

  * `.name`  The name of `C`
  * `.parameter` A parameter describing `C`. Sometimes the same as `.name`; a partition describing the Jordan form, for classical groups.
  * `.dimBu` The dimension of the variety of Borel subgroups containing `u`.

For  some  classes  in  types  `E₆,  E₇,  E₈`  there  is  a field `.mizuno` containing the names given by Mizuno for some classes, and for some classes in type `F₄` a field `.shoji` containing the names given by Shoji.

A  `UnipotentClass` contains also some of  the following information (all of it for some types and some characteristics but sometimes much less)

  * `.dynkin` the Dynkin-Richardson diagram of `C` (a vector giving a weight 0, 1 or 2 to the simple roots).
  * `.dimred` the dimension of the reductive part of `C_G(u)`.
  * `.red` a `CoxeterCoset` recording the type of the reductive part of `C_G(u)`, with the twisting induced by the Frobenius if any.
  * `.Au` the group `A_G(u)=C_G(u)/C^0_G(u)`.
  * `.balacarter` encodes the Bala-Carter classification of `C`, which says that `u` is distinguished in a Levi `L` (the Richardson class in a parabolic `P_L`) as a vector listing the indices of the simple roots in `L`, with those not in `P_L` negated.
  * `.rep` a list of indices for roots such that if `U=UnipotentGroup(W)` then `prod(U,u.rep)` is a representative of `C` (which can be obtained also by `representative(W,u)`).
  * `.dimunip` the dimension of the unipotent part of `C_G(u)`.
  * `.AuAction` an `ExtendedCoxeterGroup` recording the action of `A_G(u)` on `red`.
