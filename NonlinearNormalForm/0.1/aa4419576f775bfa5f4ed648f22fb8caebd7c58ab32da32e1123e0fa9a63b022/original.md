VectorField(h::TPS; Q::Union{Quaternion,Nothing}=nothing, spin::Union{Bool,Nothing}=nothing)

Constructs a `VectorField` from the passed Hamiltonian `h`. Explicity,  for `h`, constructs a vector field `F` such that

`F.x = [-∂h/∂p₁, ∂h/∂q₁, ...]`
