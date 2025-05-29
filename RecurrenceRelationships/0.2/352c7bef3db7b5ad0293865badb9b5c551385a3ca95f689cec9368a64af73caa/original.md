clenshaw!(f::AbstractVecOrMat, c::AbstractVecOrMat, A, B, C, x::Number)

evaluates the orthogonal polynomial expansion with coefficients `c` at points `x`, where `A`, `B`, and `C` are `AbstractVector`s containing the recurrence coefficients as defined in DLMF, overwriting `f` with the results.

If `c` is a matrix this treats each row (if `size(f,2) == 1`) or column (if `size(f,1) == 1`)` as a separate vector of coefficients.
