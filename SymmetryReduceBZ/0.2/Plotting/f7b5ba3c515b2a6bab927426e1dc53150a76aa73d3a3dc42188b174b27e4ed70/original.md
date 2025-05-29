```
plot_convexhulls(real_latvecs,atom_types,atom_pos,coords,makeprim,convention;rtol,atol)
```

Plot the Brillouin and Irreducible Brillouin zone in 2D or 3D.

!!! note "Julia 1.9 and above"
    This function is implemented in a package extension and requires `using PyPlot`.


# Arguments

  * `real_latvecs::AbstractMatrix{<:Real}`: the basis of a real-space lattice as   columns of a matrix.
  * `atom_types:AbstractVector{<:Int}`: a list of atom types as integers.
  * `atom_pos::AbstractMatrix{<:Real}`: the positions of atoms in the crystal   structure as columns of a matrix.
  * `coords::String`: indicates the positions of the atoms are in "lattice" or   "Cartesian" coordinates.
  * `makeprim::Bool=false`: make the unit cell primitive before calculating the   the IBZ if equal to `true`.
  * `convention::String="ordinary"`: the convention used to go between real and   reciprocal space. The two conventions are ordinary (temporal) frequency and   angular frequency. The transformation from real to reciprocal space is   unitary if the convention is ordinary.
  * `library::Polyhedra.Library=CDDLib.Library()`: a polyhedron manipulation library
  * `rtol::Real=sqrt(eps(float(maximum(real_latvecs))))` a relative tolerance for   floating point comparisons.
  * `atol::Real=1e-9`: an absolute tolerance for floating point comparisons.

# Returns

  * `ax::PyObject`: an updated `ax` with plots of the BZ and IBZ.

# Examples

```julia
ENV["MPLBACKEND"]="qt5agg"
using PyPlot
using SymmetryReduceBZ
real_latvecs = [1 0; .5 1]
atom_types=[0]
atom_pos = Array([0 0]')
coords = "Cartesian"
makeprim = true
convention = "ordinary"
ax=plot_convexhulls(real_latvecs,atom_types,atom_pos,coords,makeprim,convention)
# output
PyObject <AxesSubplot: >
```
