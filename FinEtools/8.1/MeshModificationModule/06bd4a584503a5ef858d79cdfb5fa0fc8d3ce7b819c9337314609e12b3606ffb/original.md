```
nodepartitioning(fens::FENodeSet, npartitions)
```

Compute the inertial-cut partitioning of the nodes.

`npartitions` = number of partitions, but note that the actual number of partitions will be a power of two.

In this variant all the nodes are to be included in the partitioning.

The partitioning can be visualized for instance as:

```julia
partitioning = nodepartitioning(fens, npartitions)
partitionnumbers = unique(partitioning)
for gp = partitionnumbers
  groupnodes = findall(k -> k == gp, partitioning)
  File =  "partition-nodes-Dollar(gp).vtk"
  vtkexportmesh(File, fens, FESetP1(reshape(groupnodes, length(groupnodes), 1)))
end
File =  "partition-mesh.vtk"
vtkexportmesh(File, fens, fes)
@async run(`"paraview.exe" DollarFile`)
```
