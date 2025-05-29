```julia
FillBZ!(bz::BZ, uc::UnitCell ; shift::Vector{Float64}=zeros(Float64, length(uc.primitives)))
```

Fills the `BZ` object with the relevant attributes, after it has been initialized with `BZ(gridSize)`.
