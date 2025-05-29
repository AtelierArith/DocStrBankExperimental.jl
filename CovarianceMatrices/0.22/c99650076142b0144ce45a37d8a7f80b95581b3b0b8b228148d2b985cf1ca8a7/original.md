Truncate(ξ::Int)

Construct a `Bartlett<:Smoother` with window half-size equal to ξ. 

Given a matrix A[i,j], its smoothed version is defined as 

$A[t, j] = \frac{1}{S_T} \sum_{s=max{t-T,-ξ}}^{min{t-1, ξ}} (1-|s/S_T|) A[t-s,j]$

where $S_T = (2\xi+1)/2$ is the bandwidth.
