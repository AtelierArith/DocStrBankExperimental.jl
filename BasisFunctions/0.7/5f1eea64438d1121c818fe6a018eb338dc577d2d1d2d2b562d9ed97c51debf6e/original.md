An `OperatedDict` represents a set that is acted on by an operator, for example the differentiation operator. The `OperatedDict` has the dimension of the source set of the operator, but each basis function is acted on by the operator.

In practice the operator `D` acts on the coefficients. Thus, an expansion in an `OperatedDict` with coefficients `c` corresponds to an expansion in the underlying dictionary with coefficients `Dc`. If `D` represents differentiation, then the `OperatedDict` effectively represents the dictionary of derivatives of the underlying dictionary elements.
