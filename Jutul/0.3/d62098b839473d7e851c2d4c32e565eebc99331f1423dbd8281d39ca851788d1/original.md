Same as [`EntityMajorLayout`](@ref), but the system is a sparse matrix where each entry is a small dense matrix.

For a test system with primary variables P, S and equations E1, E2 and two cells this will give a diagonal of length 2: [(∂E1/∂p)₁ (∂E1/∂S)₁ ; (∂E2/∂p)₁ (∂E2/∂S)₁] [(∂E1/∂p)₂ (∂E1/∂S)₂ ; (∂E2/∂p)₂ (∂E2/∂S)₂]
