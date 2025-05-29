Multiple Counts Distributed Multinomial Regression by running independent poisson gamma lasso regression to each column of counts, picks the minimum AICc segement of each path, and returns a coefficient matrix (coefs) representing point estimates for the entire multinomial (includes the intercept if one was included). Unlike dmr(), mcdmr() takes a vector of counts matrices and sequencially

1. regresses each counts matrix on the covars genrating an srproj Z (includes total counts m)
2. accumulated srproj z into Z
3. uses [covars Z] for subsequent regressions

Returns the accumulated Z matrix and a vector of coefficient matrices
