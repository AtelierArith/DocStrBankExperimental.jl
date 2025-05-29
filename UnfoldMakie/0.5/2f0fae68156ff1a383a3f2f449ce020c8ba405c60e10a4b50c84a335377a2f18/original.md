```
to_positions(x, y, z; sphere = [0, 0, 0.])
to_positions(pos::AbstractMatrix; sphere = [0, 0, 0.])
```

Projects 3D electrode positions to a 2D layout. Reimplementation of the MNE algorithm.

Assumes `size(pos) = (3, nChannels)` when input is `AbstractMatrix`.

Tip: You can get positions directly from an MNE object after loading PyMNE and enabling the UnfoldMakie PyMNE extension.

**Return Value:** `Vector{Point2{Float64}}`. 
