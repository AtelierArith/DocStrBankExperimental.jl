# ribbon_graph

```julia
ribbon_graph(d; m, c)

```

Ribbon graphs after marginalization and conditioning.

### Required arguments

```julia
* `d::DAG`                             : DAG onject
```

### Optional arguments

```julia
* `m::Vector{Symbol}`                  : Nodes in DAG that are marginalized
* `c::Vector{Symbol})`                 : Nodes in DAG there are conditioned on
```

### Returns

```julia
* `rg::NamedArray`                     : Ribbon graph remaining
```
