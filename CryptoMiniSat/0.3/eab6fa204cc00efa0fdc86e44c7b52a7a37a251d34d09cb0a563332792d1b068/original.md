`add_clause(p::CMS, clause::Vector{Union{CMSLit,Integer}})::Bool`

Add a clause to the system, namely the disjunction of the entries in `clause`. Direct terms are integers are numbered from 1, inverted terms are negative numbered from -1. They may also be specified as `CMSLit(variable,invert)`.
