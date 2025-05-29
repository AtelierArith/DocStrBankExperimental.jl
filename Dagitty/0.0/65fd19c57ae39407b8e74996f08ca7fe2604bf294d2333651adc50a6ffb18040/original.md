```
is_d_separated(dag, x, y, cond)
```

Checks that X variables are independent on Y variables being conditioned on third set of variables. Three sets could be given as vectors of node labels (`Symbol`) or as vectors of node indices in the underlying graph. Used NetworkX `d_separated` implementation.

# Examples

```jldoctest
julia> using Dagitty

julia> g = DAG(:A => :C, :C => :B)
DAG: {3, 2} directed simple Int64 graph with labels [:A, :B, :C])

julia> is_d_separated(g, [:A], [:B], [:C])
true

julia> is_d_separated(g, [:A], [:C], [:B])
false

julia> is_d_separated(g, [1], [2], [3])
true
```
