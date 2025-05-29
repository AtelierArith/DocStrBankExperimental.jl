beta=BettiNumbers(D::DirectedComplex,maximaldimension=Inf) This function returns the Betti numbers of the homology of a   directed complex using an interface to PHAT

Here the length of beta is equal to maximaldimension+1, beta[1] is 0-th Betti number  and beta[P.dim+1] is the P.dim-dimensional Betti number maximaldimension is an optional parameter to restrict the maximal possible dimension of homology to compute
