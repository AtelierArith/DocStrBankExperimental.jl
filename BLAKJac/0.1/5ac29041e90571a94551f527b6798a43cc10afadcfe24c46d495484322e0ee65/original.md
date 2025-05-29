```
TrajectorySet(ky::Vector{Float64}, kz::Vector{Float64})
```

Converts two arrays ky and kz into a set of (single-element) 'trajectories'

The arrays have to be of the same length: the number of profiles acquired during the sequence. If 2D sequences are considered, kz  can be initialized by kz=ones(nTR). The values can be provided 'signed' (e.g. ky ranging from -112 to +111) or 'unsigned'  (e.g. ranging from 1 to 224). In the latter case, the range of each array is first translated to a symmetric range around 0.
