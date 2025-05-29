```
MPOHamiltonian(lattice::AbstractArray{<:VectorSpace}, local_operators...)
MPOHamiltonian(lattice::AbstractArray{<:VectorSpace})
MPOHamiltonian(x::AbstractArray{<:Any,3})
```

MPO representation of a hamiltonian. This is a specific form of an [`AbstractMPO`](@ref), where all the sites are represented by an upper triangular block matrix of the following form:

$$
\begin{pmatrix}
1 & C & D \\
0 & A & B \\
0 & 0 & 1
\end{pmatrix}
$$

where `A`, `B`, `C`, and `D` are `MPOTensor`s, or (sparse) blocks thereof.

## Examples

For example, constructing a nearest-neighbour Hamiltonian would look like this:

```julia
lattice = fill(ℂ^2, 10)
H = MPOHamiltonian(lattice, (i, i+1) => O for i in 1:length(lattice)-1)
```

See also [`instantiate_operator`](@ref), which is responsable for instantiating the local operators in a form that is compatible with this constructor.
