```
readmultinewick(filename::AbstractString, fast=true)
readmultinewick(newicktrees_list::Vector{<:AbstractString})
```

Read a list of networks in parenthetical format, either from a file (one network per line) if the input is a string giving the path to the file, or from a vector of strings with each string corresponding to a newick-formatted topology. By default (`fast=true`), `Functors.fmap` is used for repeatedly reading the newick trees into of HybridNetwork-type objects. The option `fast=false` corresponds to the behavior up until v0.14.3: with a file name as input, it prints a message (without failing) when a phylogeny cannot be parsed, and allows for empty lines. Each network is read with [`readnewick`](@ref).

Return an array of HybridNetwork objects.

# Examples

```julia
julia> multitreepath = joinpath(dirname(Base.find_package("PhyloNetworks")), "..", "examples", "multitrees.newick");
julia> multitree = readmultinewick(multitreepath) # vector of 25 HybridNetworks
julia> multitree = readmultinewick(multitreepath, false) # same but slower & safer
julia> treestrings = readlines(multitreepath) # vector of 25 strings
julia> multitree = readmultinewick(treestrings)
julia> readmultinewick(treestrings, false) # same, but slower
```
