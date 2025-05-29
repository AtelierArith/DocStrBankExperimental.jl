Create a CausalLoopPol from a vector of node names, and two vectors indicating which indices for vertices will act as edges.

to_clp([:A, :B], [1 => 2], Vector{Pair{Int, Int}}()) will create a CausalLoopPol with a positive polarity edge from A to B.
