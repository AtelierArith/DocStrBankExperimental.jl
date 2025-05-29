# ribbon_graph

```julia
ribbon_graph(amat; m, c)

```

Ribbon graphs after marginalization and conditioning.

### Required arguments

```julia
* `amat::NamedArray{Int, 2}`           : Adjacency matrix of a DAG
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

# Extended help

### Example

### Adjacency matrix used for testing in ggm

```julia
amat_data = transpose(reshape([
  0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,
  0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,
  1,1,0,0,0,0,0,0,0,0,0,0,0,0,0,0,
  0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,
  0,0,0,1,0,0,0,0,0,0,0,0,0,0,0,0,
  0,1,0,0,1,0,0,0,0,0,0,0,0,0,0,0,
  0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,
  0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,
  0,0,0,0,0,0,1,1,0,0,0,0,0,0,0,0,
  0,0,0,0,0,0,0,1,0,0,0,0,0,0,0,0,
  0,0,0,0,1,0,1,0,1,1,0,0,0,0,0,0,
  1,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,
  0,0,0,0,0,0,0,0,0,1,0,1,0,0,0,0,
  0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,
  1,0,0,0,0,0,0,0,0,0,0,0,0,1,0,0,
  0,0,0,0,0,0,0,0,0,0,0,1,0,1,0,0
], (16,16)));

vars = [Symbol("n\$i") for i in 1:size(amat_data, 1)]
amat = NamedArray(Int.(amat_data), (vars, vars), ("Rows", "Cols"));
m = [:n3, :n5, :n6, :n15, :n16];
c = [:n4, :n7];

rg = ribbon_graph(amat; m = m, c = c)
```

### Acknowledgements

Original author:                       Kayvan Sadeghi

Translated to Julia:                   Rob J Goedman

### References

Sadeghi, K. (2011). Stable classes of graphs containing directed acyclic graphs.

Richardson, T.S. and Spirtes, P. (2002).  Ancestral graph Markov models {Annals of Statistics}, 30(4), 962-1030.

Sadeghi, K. and Lauritzen, S.L. (2011). [Markov properties for loopless mixed graphs](http://arxiv.org/abs/1109.5909).

### Licence

The R package ggm is licensed under License: GPL-2.

The Julia translation is licenced under: MIT.

Part of the api, exported.
