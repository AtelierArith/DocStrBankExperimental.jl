```julia
saveDFG(folder, dfg; saveMetadata)

```

Save a DFG to a folder. Will create/overwrite folder if it exists.

DevNotes:

  * TODO remove `compress` kwarg.

# Example

```julia
using DistributedFactorGraphs, IncrementalInference
# Create a DFG - can make one directly, e.g. GraphsDFG{NoSolverParams}() or use IIF:
dfg = initfg()
# ... Add stuff to graph using either IIF or DFG:
v1 = addVariable!(dfg, :a, ContinuousScalar, tags = [:POSE], solvable=0)
# Now save it:
saveDFG(dfg, "/tmp/saveDFG.tar.gz")
```
