```julia
loadDFG!(
    dfgLoadInto,
    dst;
    overwriteDFGMetadata,
    useDeprExtract
)

```

Load a DFG from a saved folder.

# Example

```julia
using DistributedFactorGraphs, IncrementalInference
# Create a DFG - can make one directly, e.g. GraphsDFG{NoSolverParams}() or use IIF:
dfg = initfg()
# Load the graph
loadDFG!(dfg, "/tmp/savedgraph.tar.gz")
# Use the DFG as you do normally.
ls(dfg)
```

See also: [`loadDFG`](@ref), [`saveDFG`](@ref)
