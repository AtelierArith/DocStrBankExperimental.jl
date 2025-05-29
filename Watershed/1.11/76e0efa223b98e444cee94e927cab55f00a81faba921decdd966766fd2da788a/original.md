`FINDBASINS` - find basins of attraction

```
 seg, counts, counts0 = findbasins(sag)
```

  * `sag`: steepest ascent graph (directed and unweighted). `sag[x,y,z]` contains 6-bit number encoding edges outgoing from (x,y,z)
  * `seg`: segmentation into basins.  Each element of the 3D array contains a *basin ID*, a nonnegative integer ranging from 0 to the number of basins.
  * `counts`: number of voxels in each basin
  * `counts0`: number of background voxels

A value of 0 in `seg` indicates a background voxel, which has no edges at all in the steepest ascent graph.  All such singletons are given the same ID of 0, although they are technically basins by themselves.

The algorithm starts from an unassigned voxel, and identifies all downstream voxels via breadth-first search (BFS). The search terminates in two possible ways:

1. downstream voxel that was previously assigned a basin ID =>

assign that ID to queued voxels.

2. no more downstream voxels => assign new basin ID to queued voxels.

Then the queue is emptied, and BFS begins anew at an unassigned voxel. The algorithm ends when all voxels are assigned.

The 7th bit (0x40) is used to indicate whether a voxel has been visited during BFS.

The MSB indicates whether a voxel has been assigned a basin ID.  The MSB definition is given in the functions at the end of the file for UInt32 and UInt64 cases.

`findbasins` is applied to the steepest ascent graph after modification by `divideplateaus!`  By this point all paths are unique, except in maximal plateaus.

# what happens if `findbasins` is applied directly to the output of `steepestascent`?  ties are resolved in an unsystematic way.  seems to differ from Cousty's watershed cuts, which alternates btw DFS and BFS.
