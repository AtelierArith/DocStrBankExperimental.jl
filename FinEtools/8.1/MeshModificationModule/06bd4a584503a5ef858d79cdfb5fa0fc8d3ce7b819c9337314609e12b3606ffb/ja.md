```
nodepartitioning(fens::FENodeSet, npartitions)
```

ノードの慣性カット分割を計算します。

`npartitions` = 分割数ですが、実際の分割数は2の累乗であることに注意してください。

このバリアントでは、すべてのノードが分割に含まれる必要があります。

分割は、例えば次のように視覚化できます：

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
