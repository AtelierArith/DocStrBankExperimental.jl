```
nodepartitioning(fens::FENodeSet, nincluded::Vector{Bool}, npartitions)
```

Compute the inertial-cut partitioning of the nodes.

`nincluded` = Boolean array: is the node to be included in the partitioning or     not? `npartitions` = number of partitions, but note that the actual number of     partitions is going to be a power of two.

The partitioning can be visualized for instance as:

```julia
partitioning = nodepartitioning(fens, npartitions)
partitionnumbers = unique(partitioning)
for gp = partitionnumbers
  groupnodes = findall(k -> k == gp, partitioning)
  File =  "partition-nodes-$(gp).vtk"
  vtkexportmesh(File, fens, FESetP1(reshape(groupnodes, length(groupnodes), 1)))
end
File =  "partition-mesh.vtk"
vtkexportmesh(File, fens, fes)
@async run(`"paraview.exe" $File`)
```
