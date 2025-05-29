```
makeswarm_genes(genes::Vector{String}; <keyword arguments> )
```

write a swarmfile and fit files to run all each gene in vector genes

# Arguments

  * `genes`: vector of genes
  * `batchsize=1000`: number of jobs per swarmfile, default = 1000

and all arguments in makeswarm(;<keyword arguments>)

```
Examples
```

julia> genes = ["MYC","SOX9"]

julia> makeswarm(genes,cell="HBEC")
