`get_conflict(p::CMS)::Vector{CMSLit}`

returns the conflicting variables in the current solution to `p`. This assumes that `solve(p)` was called and returned `false`
