```
makeWaveletGrid!(tsg::TasmanianSG; order=1, level_limits=Vector{Int32}(undef, 0))
```

creates a new sparse grid using a wavelet rule discards any existing grid held by `tsg`

order: Int (must be 1 or 3)        only wavelets of order 1 and 3 are implemented
