```
calc_bz(real_latvecs,atom_types,atom_pos,coordinates,bzformat,makeprim,
    convention,library;rtol,atol)
```

Calculate the Brillouin zone for the given real-space lattice basis.

# Arguments

  * `real_latvecs::AbstractMatrix{<:Real}`: the real-space lattice vectors or   primitive translation vectors as columns of a 2x2 or 3x3 matrix.
  * `atom_typesAbstractVector{<:Int}`: a list of atom types as integers.
  * `atom_pos::AbstractMatrix{<:Real}`: the positions of atoms in the crystal   structure as columns of a matrix.
  * `coordinates::String`: indicates the positions of the atoms are in "lattice"   or "Cartesian" coordinates.
  * `bzformat::String`: the format of the Brillouin zone. Options include   "convex hull" and "half-space".
  * `makeprim::Bool=false`: make the unit cell primitive before calculating the   the BZ if equal to `true`.
  * `convention::String="ordinary"`: the convention used to go between real and   reciprocal space. The two conventions are ordinary (temporal) frequency and   angular frequency. The transformation from real to reciprocal space is   unitary if the convention is ordinary.
  * `library::Polyhedra.Library=CDDLib.Library()`: a polyhedron manipulation library
  * `rtol::Real=sqrt(eps(float(maximum(real_latvecs))))` a relative tolerance for   floating point comparisons.
  * `atol::Real=1e-9`: an absolute tolerance for floating point comparisons.

# Returns

  * `bz`: a polyhedron conforming to the Polyhedra.jl interface that represents the convex hull of the Brillouin zone.

# Examples

```jldoctest
using SymmetryReduceBZ
real_latvecs = [1 0; 0 1]
convention="ordinary"
atom_types=[0]
atom_pos = Array([0 0]')
coordinates = "Cartesian"
makeprim=false
SymmetryReduceBZ.Symmetry.calc_bz(real_latvecs,atom_types,atom_pos,coordinates,
    makeprim,convention)
# output
Polyhedron CDDLib.Polyhedron{Float64}:
25-element iterator of Polyhedra.HalfSpace{Float64, Vector{Float64}}:
 HalfSpace([-2.0, -2.0], 4.0)
 HalfSpace([-2.0, -1.0], 2.5)
 HalfSpace([-2.0, 0.0], 2.0)
 HalfSpace([-2.0, 1.0], 2.5)
 HalfSpace([-2.0, 2.0], 4.0)
 HalfSpace([-1.0, -2.0], 2.5)
 HalfSpace([-1.0, -1.0], 1.0)
 HalfSpace([-1.0, 0.0], 0.5)
 HalfSpace([-1.0, 1.0], 1.0)
 HalfSpace([-1.0, 2.0], 2.5)
 HalfSpace([0.0, -2.0], 2.0)
 HalfSpace([0.0, -1.0], 0.5)
 HalfSpace([0.0, 0.0], 0.0)
 HalfSpace([0.0, 1.0], 0.5)
 HalfSpace([0.0, 2.0], 2.0)
 HalfSpace([1.0, -2.0], 2.5)
 HalfSpace([1.0, -1.0], 1.0)
 HalfSpace([1.0, 0.0], 0.5)
 HalfSpace([1.0, 1.0], 1.0)
 HalfSpace([1.0, 2.0], 2.5)
  ⋮:
4-element iterator of Vector{Float64}:
 [0.5, 0.5]
 [0.5, -0.5]
 [-0.5, -0.5]
 [-0.5, 0.5]
```
