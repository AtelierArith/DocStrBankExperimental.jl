`add_xor_clause(p::CMS, clause::Vector{Union{CMSLit,Int}}, rhs::Bool)::Bool`

`p`にXOR節を追加します。この節は`x_1 ⊻ x_2 ⊻ ... ⊻ x_n = rhs`の形です。
