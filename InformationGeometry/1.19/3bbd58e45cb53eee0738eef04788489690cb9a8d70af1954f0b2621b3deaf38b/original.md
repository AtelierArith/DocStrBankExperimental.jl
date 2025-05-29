```
StructurallyIdentifiable(DM::AbstractDataModel, mle::AbstractVector{<:Number}=MLE(DM); showall::Bool=false, noise::Real=1e-5, thresh::Real=1e-12, N::Int=3)
```

Checks if jacobian of model wrt parameters has singular values below threshold and provides associated singular directions.
