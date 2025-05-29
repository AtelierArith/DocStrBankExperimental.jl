ANND*out(A::T, vs=1:size(A,1); check*dimensions::Bool=true, check_directed::Bool=true) where {T<:AbstractMatrix}

Return a vector corresponding to the average nearest neighbor outdegree (ANND) all nodes in the graph with adjacency matrix `A`.  If v is specified, only return the ANND_out for nodes in v. 

See also: [`ANND_in`](@ref), [`ANND`](@ref)
