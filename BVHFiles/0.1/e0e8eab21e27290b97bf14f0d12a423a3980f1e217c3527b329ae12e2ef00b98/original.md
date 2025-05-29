```
change_sequence!(g::BVHGraph, v::Integer, sym::Symbol)
```

Change the rotation order of vertex `v` to `sym`. The euler angles are adjusted accordingly.

Valid Symbols are `:XYZ`, `:XYX`, `:XZX`, `:XZY`, `:YXZ`, `:YZX`, `:YXY`, `:YZY`,  `:ZXY`, `:ZYX`, `:ZXZ`, `:ZYZ`.

See also: [`change_sequences!`](@ref)
