maximum*weight*matching(g::Graph, w::Dict{Edge,Real} -> Dict{Edge,Int64}

Given a graph `g` and an edgemap `w` containing weights associated to edges, returns a matching with the maximum total weight. `w` is a dictionary that maps edges i => j to weights. If no weight parameter is given, all edges will be considered to have weight 1 (results in max cardinality matching)

The efficiency of the algorithm depends on the input graph:

  * If the graph is bipartite, then the LP relaxation is integral.
  * If the graph is not bipartite, then it requires a MIP solver and

the computation time may grow exponentially.

The package JuMP.jl and one of its supported solvers is required.

Returns MatchingResult containing:

  * a solve status (indicating whether the problem was solved to optimality)
  * the optimal cost
  * a list of each vertex's match (or -1 for unmatched vertices)
