GenLinearAlgebra: linear algebra over arbitrary fields and rings

The  linear  algebra  package  in  Julia  is  not  suitable  for  a general mathematics  package: it assumes  the field is  the Real or Complex numbers and  uses floating  point to  do approximate  computations. For example the invertible  rational matrix `[1//(n+m) for  n in 1:11, m  in 1:11]` has for `LinearAlgebra` a `rank` of 10 and a `Float64` nullspace of dimension 1.

Here we are interested in functions which work over any field (or sometimes any ring) and assume exact computations.

For more information, look at the helpstrings of `echelon!, rowspace, independent_rows, in_rowspace, intersect_rowspace,  lnullspace, GenLinearAlgebra.nullspace, GenLinearAlgebra.rank, solutionmat,   charpoly, comatrix, permanent, symmetric_power, exterior_power, ratio,   diagconj_elt, transporter, bigcell_decomposition, traces_words_mats, all_ge_1`.
