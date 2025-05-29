```
buildcircuit(
  hilbert::Vector{<:Index},
  circuit::Union{Tuple, Vector{<:Any}};
  noise::Union{Nothing, Tuple, NamedTuple} = nothing
)
buildcircuit(M::Union{MPS,MPO,ITensor}, args...; kwargs...)
```

Compile a circuit from a lazy representation into a vector of `ITensor`. For example, a gate element of `circuit`, `("gn", (i,j))` is turned into a rrank-4 tensor corresponding to the `i` and `j` element of `hilbert`.

If `noise` is passed, the corresponding Kraus operator are inserted appropriately after the gates in the circuit.
