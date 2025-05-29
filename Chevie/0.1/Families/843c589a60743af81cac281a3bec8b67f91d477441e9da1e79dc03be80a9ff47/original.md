`twisted_drinfeld_double_cyclic(n,ζ,piv=[1,1])`

compute  the modular  data of  the category  of modules  over the twisted Drinfeld double of a cyclic group G of order n

arguments are `(n,ζ,piv=[1,1])`, where `n` is the order of the group, `ζ`  is the value of the 3-cocycle on `(ζₙ,ζₙⁿ⁻¹,ζₙⁿ⁻¹)` and  `piv` is a pivotal structure different form the usual one (on vector spaces)

The result is a `GapObj` with fields:    .group: the group    .cocycle: `ζ`, the value of the 3-cocycle on the element `(ζₙ,ζₙ,ζₙⁿ⁻¹)`    .pivotal: a pair `[k,alpha]` where the 2-cocycle associated with `k` is a      coboundary  (an  integer  in  `0:n-1`),  and alpha the corresponding      1-cocycle  (a n^2-th root of unity)  (for the cyclic group, the Schur      multiplier  is trivial,  therefore these  pairs correspond exactly to      simple objects of the category)    .charparams: labels of lines of the fourier matrix by      pairs [x,chi]: elt of  G, projective character of G for the      corresponding cocycle     .special is the position of the special line (here 1 where (x,chi)=(1,1) is)    .eigenvalues are the eigenvalues chi(x)/chi(1)       (inverse of the T-matrix of the category)    .fourierMat is the Fourier matrix (renormalized S-matrix)   .bar  is  the  object  \overline{1}  needed  to renormalise the S-matrix     (related to the non sphericity of the pivotal structure)

In general, we have the relation `(ST)³=τ id`, where the explicit value  of `τ` can be computed using Gauss sums.
