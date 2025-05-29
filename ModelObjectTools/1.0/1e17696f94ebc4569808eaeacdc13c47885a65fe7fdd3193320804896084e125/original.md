addVarInfo(varName::Symbol; lb = -Inf, ub = Inf, normalization::Symbol = :none)

Use this function to register the variable names that will correspond  to fields in the structures defining model objects (parameter sets, sets of  endogenous variables, etc.). For each variable, the allowed range of values is [lb, ub].

If bounds are not needed, use the default options: lb = -Inf, ub = Inf.

The allowed normalization values are:

  * :sumToOne     (for unidimensional arrays)
  * :firstIsZero  (for unidimensional arrays)
  * :firstIsOne   (for unidimensional arrays)
  * :ordered      (for unidimensional arrays or matrices. With matrices, it means               the values must be increasing along columns)
  * :none         (the default option)
