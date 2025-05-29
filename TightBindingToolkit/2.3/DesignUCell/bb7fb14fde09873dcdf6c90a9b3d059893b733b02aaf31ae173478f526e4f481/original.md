```julia
ModifyBonds!(uc::UnitCell, dist::Float64, newMat::Matrix{<:Number})
ModifyBonds!(uc::UnitCell, label::String, newMat::Matrix{<:Number})
```

Modify an existing bond in the `UnitCell` with the given `label`, or at a given distance=`dist`, to the given bond matrix.
