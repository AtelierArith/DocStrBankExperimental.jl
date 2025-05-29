get*normal*dense*chol*suff_stats(x::AbstractMatrix{<:Real})

Returns the sufficients statistics for a multivariate normal with dense covariance matrix. Note that the cholesky of the sample covariance is the "biased" version (divided by n, instead of n - 1).
