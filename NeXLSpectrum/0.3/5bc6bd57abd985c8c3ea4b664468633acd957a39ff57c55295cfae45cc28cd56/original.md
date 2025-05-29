The TopHatFilter{T <: AbstractFloat} struct represents a zero-sum symmetric second-derivative-like filter that when  applied to spectral data has the property of suppressing constant and slowly varying signals (like the continuum) while retaining a linear signal for faster changing signals like the characteristic peaks.

See

  * F. H. Schamber Proc Symposium of "X-ray Fluorscence Analysis on Environmental Samples" Chapel Hill 1976 T Dzubay Ed.
  * P. Statham Anal Chem 49 no 14 Dec 1977

The TopHatFilter struct optimizes the memory and CPU use when applying top-hat filters to spectrum data.

The easiest way to implement a top-hat filter is as matrix F.  The rows represent the filters.  The product of the filter and the data vector is the filtered spectrum.  The product of the filter times a diagnonal matrix constructed from the data times the transpose of the filter is the covariance of the filtered data.  The diagonal matrix constructed from the spectrum data is the covariance matrix associated with the spectrum data because the channels in the spectrum data are independent (thus the matrix is diagnonal) and the magnitude equals the counts in each channels because the spectrum data is nominally Poissonian and in the large number limit, the variance of a Poissonian random variable is the number itself (σ=sqrt(N) => Var = N)

Notes on memory and code optimization: The filter matrix is banded diagonal.  Approximately, 2.5% of the elements are non-zero.  This suggest use of the BandedMatrix type.  The most expensive operation is calculating F⋅D⋅Fᵀ, the covariance matrix of the filtered data. D is a diagonal matrix and so computing each element in F⋅D⋅Fᵀ reduces to a sum over a single variable. Furthermore, the weighted least squares fit doesn't require the full F⋅D⋅Fᵀ, just diag(F⋅D⋅Fᵀ).  However, it turns out that we can do better implementing our own banded matrix type largely because D is fully diagonal and the matrix product F⋅D⋅Fᵀ reduces down to a sum over a single variable.  The product F⋅d and F⋅D⋅Fᵀ are readily implemented as element-by-element multiplies and sums.  Thus storing the filter as offsets and row filters is efficient in both memory and CPU use.
