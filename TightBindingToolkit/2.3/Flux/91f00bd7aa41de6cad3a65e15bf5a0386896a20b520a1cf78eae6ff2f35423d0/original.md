```julia
ModifyGauge!(lat::Lattice{T}, A::Function ; n::Int64 = 100, _kwargs::Dict = Dict()) where{T}
```

Modifies the lattice hoppings using the fixed gauge vector potential `A` on the lattice `lat` by multiplying the bond matrices with the corresponding phase factors.
