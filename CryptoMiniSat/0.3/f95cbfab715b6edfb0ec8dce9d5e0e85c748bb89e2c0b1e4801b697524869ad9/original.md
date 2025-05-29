`get_model(p::CMS)::Vector{Bool}`

returns the variables in the current solution to `p`. This assumes that `solve(p)` was called and returned `true`.
