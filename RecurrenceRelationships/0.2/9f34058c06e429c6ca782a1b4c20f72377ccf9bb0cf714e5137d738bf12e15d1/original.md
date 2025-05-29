clenshaw!(f, c, A, B, C, x, ϕ₀)

evaluates the orthogonal polynomial expansion with coefficients `c` at point `x`, where `A`, `B`, and `C` are `AbstractVector`s containing the recurrence coefficients as defined in DLMF and ϕ₀ is the zeroth polynomial, overwriting `f` with the results.
