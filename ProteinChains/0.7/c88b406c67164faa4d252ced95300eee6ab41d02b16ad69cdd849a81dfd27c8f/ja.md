```
IdealResidue{T<:AbstractFloat} <: AbstractMatrix{T}

IdealResidue{T}(backbone_geometry=DEFAULT_BACKBONE_GEOMETRY; template=nothing) where T
```

原点に位置する残基のN、Ca、C原子の位置を表す列を持つ、タンパク質残基の理想化された幾何学を表す3x3行列。
