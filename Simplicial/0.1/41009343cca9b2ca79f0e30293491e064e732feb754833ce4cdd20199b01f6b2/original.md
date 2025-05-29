beta=BettiNumbers*naive*method(D::DirectedComplex,maximaldimension=Inf)

This function returns the Betti numbers of the homology of a (so far only pure) directed complex This is a very crude way to compute directed homology – this does not use any tricks, just the definition and the built-in rank function that may fail to work properly on large enough matrices. Use with caution. Works as prescribed on small enough complexes.

Here the length of beta is equal to maximaldimension+1, beta[1] is 0-th Betti number  and beta[P.dim+1] is the P.dim-dimensional Betti number maximaldimension is an optional parameter to restrict the maximal possible dimension of homology to compute
