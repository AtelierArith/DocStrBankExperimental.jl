```
change_sequences!(g::BVHGraph, sym::Symbol)
```

Change the rotation order of all vertices to `sym`. The euler angles are adjusted accordingly.

Valid Symbols are `:XYZ`, `:XYX`, `:XZX`, `:XZY`, `:YXZ`, `:YZX`, `:YXY`, `:YZY`,  `:ZXY`, `:ZYX`, `:ZXZ`, `:ZYZ`.

See also: [`change_sequence!`](@ref)
