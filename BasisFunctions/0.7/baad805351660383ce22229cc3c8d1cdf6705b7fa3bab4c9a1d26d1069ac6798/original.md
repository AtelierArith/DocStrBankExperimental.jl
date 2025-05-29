A BlockOperator has a block matrix structure, where each block is an operator, and it acts on multiple sets.

A BlockOperator is row-like if it only has one row of blocks. In that case, the destination of the operator is not necessarily a multidict.

A BlockOperator is column-like if it only has one column of blocks. In that case, the source set of the operator is not necessarily a multidict.
