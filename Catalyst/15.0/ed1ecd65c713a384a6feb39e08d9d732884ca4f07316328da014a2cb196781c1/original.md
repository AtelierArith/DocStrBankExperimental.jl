```
make_edge_p_values(lrs::LatticeReactionSystem, make_edge_p_value::Function)
```

Generates edge parameter values for a lattice reaction system. Only work for (Cartesian or masked) grid lattices (without diagonal adjacencies).

Input:

  * `lrs`: The lattice reaction system for which values should be generated.

      * `make_edge_p_value`: a function describing a rule for generating the edge parameter values.

Output:     - `ep_vals`: A sparse matrix of size (num*verts,num*verts) (where num*verts is the number of     vertices in `lrs`). Here, `eps[i,j]` is filled only if there is an edge going from vertex i to     vertex j. The value of `eps[i,j]` is determined by `make*edge*p*value`.

Here, `make_edge_p_value` should take two arguments, `src_vert` and `dst_vert`, which correspond to the grid indices of an edge's source and destination vertices, respectively. It outputs a single value, which is the value assigned to that edge.

Example:     In the following example, we assign the value `0.1` to all edges, except for the one leading from     vertex (1,1) to vertex (1,2), to which we assign the value `1.0`.

```julia
using Catalyst
rn = @reaction_network begin
    (p,d), 0 <--> X
end
tr = @transport_reaction D X
lattice = CartesianGrid((5,5))
lrs = LatticeReactionSystem(rn, [tr], lattice)

function make_edge_p_value(src_vert, dst_vert)
    if src_vert == (1,1) && dst_vert == (1,2)
        return 1.0
    else
        return 0.1
    end
end

D_vals = make_edge_p_values(lrs, make_edge_p_value)
```
