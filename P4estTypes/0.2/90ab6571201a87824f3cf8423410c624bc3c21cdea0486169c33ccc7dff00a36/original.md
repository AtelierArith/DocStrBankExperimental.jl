```
pxest(connectivity::Connectivity{X}; kw...) where {X}
```

Generate a distributed forest of quadtrees (if `X=4`) or octrees (if `X=8`) based on `connectivity`.  Each element of `connectivity` becomes a tree root.

The connectivity is duplicated on all ranks but the leaves of the forest are split (based on a space-filling curve order) among the ranks.

The keyword arguments (`kw...`) that control the construction of the forest are:

  * `comm = MPI.COMM_WORLD`: the MPI Communicator object of the ranks sharing  the forest.
  * `min_quadrants = 0`: the minimum number of quadrants per rank.  (This makes the initial refinement pattern `MPI.Comm_size` specific.)
  * `min_level = 0`: the minimum level of quadrant refinement for the forest.
  * `fill_uniform = true`: if `true` the forest will be filled with a uniform mesh otherwise it is the coarsest possible mesh.
  * `data_type = Nothing`: an `isbitstype` of the user data stored for each quadrant.
  * `init_function = nothing`: callback function with prototype `init_function(forest, treeid, quadrant)` called for each quadrant to initialized the user data.
