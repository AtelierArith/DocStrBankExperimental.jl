```
updateSequenceGrid!(tsg::TasmanianSG, depth, type; anisotropic_weights=Vector{Int32}(undef, 0), level_limits=Vector{Int32}(undef, 0))
```

adds the points defined by depth, type and anisotropy to the existing grid

basically, the same as calling makeSequenceGrid() with rule,            of this grid and the new depth, type and            anisotropic_weights then adding the resulting points            to the current grid

inputs: see help(makeSequenceGrid)
