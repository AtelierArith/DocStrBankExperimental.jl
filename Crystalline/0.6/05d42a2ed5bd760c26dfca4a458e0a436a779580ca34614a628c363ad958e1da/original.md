```
surface_basis(Rs, n; cartesian=true)
```

Compute a basis for the surface-cell obtained from terminating a 3D lattice `Rs` over a surface surface specified by its normal vector `n` (or Miller indices if `cartesian=false`).

## Output

The function returns a tuple `(rs³ᴰ, rs′²ᴰ, P)`, whose elements are described below:

  * `rs³ᴰ`: a `DirectBasis{3}`, whose first two basis vectors lie in the plane of the surface, and whose third vector is (positively) aligned with the surface normal. All basis vectors correspond to points in the original direct lattice.
  * `rs′²ᴰ`: a `DirectBasis{2}`, whose basis vectors are given in the local coordinate system of the surface unit cell; effectively, this is $(x,y)$-components of `rs³ᴰ` after a rotation that takes `n` to $\hat{\mathbf{z}}$. The first basis vector is aligned with the $\hat{\mathbf{x}}$-direction of the local coordinate system.
  * `P`: a rotation matrix that takes `rs³ᴰ` to the local `n`-to-$\hat{\mathbf{z}}$ rotated coordinate system of `rs′²ᴰ`. In particular, defining `rs′³ᴰ = transform.(DirectPoint.(rs³ᴰ), Ref(P))`, the following  holds: 	- `rs′³ᴰ[i] ≈ [rs′²ᴰ[i]..., 0]` for `i ∈ 1:2`, 	- `rs′³ᴰ[3]` is (positively) aligned with `[0,0,1]`. To transform the other way, i.e., from surface-local to lattice-global coordinates, simply use `P⁻¹ = transpose(P)` instead.

The returned basis is right-handed.

## Keyword arguments

  * `cartesian :: Bool = true`: whether the surface normal `n` is specified in Cartesian coordinates (`true`) or in the basis of the reciprocal lattice vectors (`false`), i.e., corresponding to the Cartesian vector `n[1]*Gs[1] + n[2]*Gs[2] + n[3]*Gs` with `Gs` denoting the Cartesian representation of the reciprocal lattice vectors, i.e., `Gs = dualbasis(Rs)`. The latter case (`false`) is a specification of the surface in terms of its Miller indices: the coordinates of `n` can then equivalently be interpreted as the inverse of the surface's intercept with each of the axes spanned by `Rs`.

## Example

```jldoctest
julia> sgnum = 195; # P23, a cubic lattice

julia> Rs = directbasis(sgnum, 3)
DirectBasis{3} (cubic):
 [1.0, 0.0, 0.0]
 [0.0, 1.0, 0.0]
 [0.0, 0.0, 1.0]

julia> n = [1,1,1]; # project along 111 direction

julia> rs³ᴰ, rs′²ᴰ, P = surface_basis(Rs, n; cartesian=true);

julia> rs³ᴰ # the surface basis in the original coordinate system
DirectBasis{3} (hexagonal):
 [1.0, -1.5700924586837747e-16, -0.9999999999999998]
 [-0.9999999999999998, 0.9999999999999997, 0.0]
 [1.0, 1.0, 1.0]

julia> rs′²ᴰ # the in-plane surface vectors in a local "surface coordinate system"
DirectBasis{2} (hexagonal):
 [1.414213562373095, 0.0]
 [-0.7071067811865475, 1.2247448713915887]

julia> DirectBasis(transform.(DirectPoint.(rs³ᴰ), Ref(P))) # from rs³ᴰ to rs′²ᴰ coordinates 
DirectBasis{3} (hexagonal):
 [1.414213562373095, -1.1102230246251563e-16, 0.0]
 [-0.7071067811865476, 1.2247448713915885, 0.0]
 [0.0, -1.1102230246251563e-16, 1.7320508075688772]
```

!!! warning
    This function will likely be moved from Crystalline to Bravais.jl at some point in the future.

