cholesky(As::Vector{SparseMatrixCSC{ComplexF64,Int}}, I::Vector{Int})

Creates a block-diagonal (lazy) array of factors. Invokes `cholesky` on each matrix in the array of matrices `As` and stores them along with the indices `I`.
