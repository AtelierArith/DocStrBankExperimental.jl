project(A::SpotOmegaWord,inds::Union{Int,Vector{Int}}) project(A::SpotAutomaton,inds::Union{Int,Vector{Int}})

Project the word or automaton by a letter-to-letter map on tuples, specified by `inds`.

For example, if `A` has alphabet `NTuples{3,Ta}`, then `project(A,[1,3])` will map the tuple `(:x,:y,:z)` to `(:x,:z)` and `project(A,2)` will map  `(:x,:y,:z)` to `:y`; while if `A` has alphabet `Ta` or `Tuple{Ta}`, then `project(A,[0,1,0,1])` map `:x`, respectively `(:x,)`, to `(Any,:x,Any,:x)`.
