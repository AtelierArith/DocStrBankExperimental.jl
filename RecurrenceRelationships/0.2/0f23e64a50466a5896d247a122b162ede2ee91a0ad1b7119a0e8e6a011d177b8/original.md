forwardrecurrence(A, B, C, x)

evaluates the first `N+1` orthogonal polynomials at point `x`, where `A`, `B`, and `C` are `AbstractVector`s containing the first form recurrence coefficients as defined in  [DLMF](https://dlmf.nist.gov/18.9) and `N` is the minimum length of `A`, `B`, and `C`, i.e. it returns Pᵢ(x) for i = 0, 1, ..., `min(length(A), length(B), length(C))`
