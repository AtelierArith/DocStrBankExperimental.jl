```
LPHGLET_dictionary(GP::GraphPart, G::GraphSig; gltype::Symbol = :L, ϵ::Float64 = 0.3)
```

assemble the whole LP-HGLET dictionary

### Input Arguments

  * `GP`: a GraphPart object
  * `G`:  a GraphSig object
  * `gltype`: `:L` or `:Lsym`
  * `ϵ`: relative action bandwidth (default: 0.3)

### Output Argument

  * `dictionary`: the LP-HGLET dictionary
