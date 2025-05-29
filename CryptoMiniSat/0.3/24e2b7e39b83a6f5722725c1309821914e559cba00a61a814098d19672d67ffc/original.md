`add_xor_clause(p::CMS, clause::Vector{Union{CMSLit,Int}}, rhs::Bool)::Bool`

Adds an XOR clause to `p`. This is a clause of the form `x_1 ⊻ x_2 ⊻ ... ⊻ x_n = rhs`.
