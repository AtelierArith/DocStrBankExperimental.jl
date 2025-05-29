```
Chamber(;
        iontrap::LinearChain, B::Real=0, Bhat::NamedTuple{(:x,:y,:z)=ẑ, ∇B::Real=0,
         δB::Union{Real,Function}=0, lasers::Vector{Laser}
)
```

Information necessary to describe the Hamiltonian for a collection of ions in a linear chain interacting with laser light. **user-defined fields**

  * `iontrap<:LinearChain`
  * `B`: A real value describing the mean magnitude of the B-field [Tesla].
  * `Bhat::NamedTuple{(:x,:y,:z)}`: Describes the direction of the B-field (defaults to ẑ).
  * `∇B`: Magnitude of the B-field gradient. We assume that the gradient always points along the       z-direction. [Tesla / meter]
  * `δB::Function`: Time-dependence of the B-field [Tesla]
  * `lasers::Array{<:Laser}`: For each laser in the array, the pointing field should contain       an array of `Tuple{Int,Real}`. The first element specifies the index of an ion       in the `ions` field that the laser interacts with. The second element specifies a       scaling factor for the strength of that interaction (to be used, e.g., for       modeling cross-talk).

**derived fields**

  * `_cnst_δB::Bool`: A Boolean flag signifying whether or not `δB` is a constant function.
  * `basis<:CompositeBasis`: The basis for describing the combined system, ions + vibrational       modes. If constructing the Hamiltonian explictly (with [`hamiltonian`](@ref)), then       the ordering of the basis is set, by convention, as       $ion₁ ⊗ ion₂ ⊗ ... ⊗ ion_N ⊗ mode₁ ⊗ mode₂ ⊗ ... ⊗ mode_N$, where the ion bases are       ordered according to the order in `T.iontrap.ions` and the vibrational modes       are ordered according to the order in       `[T.iontrap.selectedmodes.x, T.iontrap.selectedmodes.y,       T.iontrap.selectedmodes.z]`.   E.g. for:

    `chain = LinearChain(ions=[C1, C2], comfrequencies=(x=2e6,y=2e6,z=1e6),   selectedmodes=(x=[1, 2], y=[], z=[1]))`

    The ordering of the basis would be

    `C1.basis ⊗ C2.basis ⊗ chain.selectedmodes.x[1].basis   ⊗ chain.selectedmodes.x[2].basis ⊗ chain.selectedmodes.z[1].basis`

    Otherwise, the ordering is according to the form of the initial state used in the solver.
