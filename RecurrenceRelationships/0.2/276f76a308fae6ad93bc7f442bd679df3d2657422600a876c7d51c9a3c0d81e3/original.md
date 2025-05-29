forwardrecurrence(N, A, B, C, x)

evaluates the first `N` orthogonal polynomials at point `x`, where `A`, `B`, and `C` are `AbstractVector`s containing the first form recurrence coefficients as defined in  [DLMF](https://dlmf.nist.gov/18.9), i.e. it returns Pᵢ(x) for i = 0, 1, ..., N-1
