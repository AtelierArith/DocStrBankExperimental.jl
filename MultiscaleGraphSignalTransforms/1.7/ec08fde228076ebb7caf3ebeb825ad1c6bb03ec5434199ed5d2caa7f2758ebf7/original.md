```
BS = bs_level(GP::GraphPart, j::Int, c2f::Bool = true)
```

Specify the basis corresponding to level j for a given graph partitioning

### Input Arguments

  * `GP::GraphPart`: an input GraphPart object
  * `j::Int`: the level to which the basis corresponds (`j = 0` is the global level)
  * `c2f::Bool`: a flag for c2f or f2c (default: true, i.e., c2f)

### Output Argument

  * `BS::BasisSpec`: a BasisSpec object corresponding to the level `j` basis
