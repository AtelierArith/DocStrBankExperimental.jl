`STEEPESTASCENT` - Construct steepest ascent graph from affinity graph

```
 sag = steepestascent(aff, low, high)
```

  * `sag`: steepest ascent graph (directed and unweighted). `sag[x,y,z]` contains 6-bit number encoding edges outgoing from (x,y,z)
  * `aff`: affinity graph (undirected and weighted). 4D array of affinities, where last dimension is of size 3
  * `low`: edges with affinity <= `low` are removed
  * `high`: affinities >= `high` are considered infinity

Directed paths in the steepest ascent graph are steepest ascent paths in the affinity graph.  Both graphs are for 3D lattice with 6-connectivity.  The steepest ascent graph can contain vertices with multiple outgoing edges if there are ties in the affinity graph, i.e., if steepest ascent paths are nonunique.

We follow the convention that:

  * `aff[x,y,z,1]` is affinity of voxels at [x-1,y,z] and [x,y,z]
  * `aff[x,y,z,2]` is affinity of voxels at [x,y-1,z] and [x,y,z]
  * `aff[x,y,z,3]` is affinity of voxels at [x,y,z-1] and [x,y,z]
