# ancestral_graph

```julia
ancestral_graph(d; m, c)

```

Ancestral graphs after marginalization and conditioning.

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
* `ag::NamedArray`                     : Ancestral graph remaining
```
