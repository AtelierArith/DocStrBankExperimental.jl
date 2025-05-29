Computes the Bayesian score component for the given target variable index and     Dirichlet prior counts given in alpha

INPUT:     i       - index of the target variable     parents - list of indeces of parent variables (should not contain self)     r       - list of instantiation counts accessed by variable index               r[1] gives number of discrete states variable 1 can take on     data - matrix of sufficient statistics / counts               d[j,k] gives the number of times the target variable took on its kth instantiation               given the jth parental instantiation

OUTPUT:     the Bayesian score, Float64
