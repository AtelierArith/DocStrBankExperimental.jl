```
maximum_flow{T<:Number}(
                    g::ADiGraph,
                    source::Int,
                    target::Int,
                    capacity_matrix::AbstractMatrix{T} =
                        DefaultCapacity(g);
                    algorithm::AbstractFlowAlgorithm  =
                        PushRelabelAlgorithm(),
                    restriction::T = zero(T)
                )
```

Generic maximum*flow function. The function defaults to the Push-Relabel (also called Preflow) algorithm. Alternatively, the algorithm to be used can also be specified through a keyword argument. A default capacity of 1 is assumed for each link if no capacity matrix is provided. If the restriction is bigger than 0, it is applied to capacity*matrix.

All algorithms return a tuple with

1. the maximum flow
2. the flow matrix
3. the labelling associated to the minimum cut

Available algorithms are `DinicAlgorithm`, `EdmondsKarpAlgorithm`, `BoykovKolmogorovAlgorithm` and `PushRelabelAlgorithm`.

Time complexity is O(V²√E) for the push relabel algorithm.

### Usage Example:

```julia

# Create a flow-graph and a capacity matrix
g = DiGraph(8)
flow_edges = [
    (1,2,10),(1,3,5),(1,4,15),(2,3,4),(2,5,9),
    (2,6,15),(3,4,4),(3,6,8),(4,7,16),(5,6,15),
    (5,8,10),(6,7,15),(6,8,10),(7,3,6),(7,8,10)
]
capacity_matrix = zeros(Int, 8, 8)
for e in flow_edges
    u, v, f = e
    add_edge!(g, u, v)
    capacity_matrix[u,v] = f
end

# Run default maximum_flow without the capacity_matrix (assumes capacity 1. on each edge).
f, F, labels = maximum_flow(g, 1, 8)

# Run Endmonds-Karp algorithm
f, F, labels = maximum_flow(g,1,8,capacity_matrix,algorithm=EdmondsKarpAlgorithm())
```
