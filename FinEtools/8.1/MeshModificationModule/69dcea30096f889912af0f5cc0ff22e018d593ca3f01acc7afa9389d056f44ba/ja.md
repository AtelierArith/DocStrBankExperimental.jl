```
nodepartitioning(fens::FENodeSet, nincluded::Vector{Bool}, npartitions)
```

ノードの慣性カット分割を計算します。

`nincluded` = ブール配列: ノードは分割に含まれるべきかどうか？ `npartitions` = 分割の数ですが、実際の分割数は2の累乗になります。

分割は例えば次のように視覚化できます：

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
