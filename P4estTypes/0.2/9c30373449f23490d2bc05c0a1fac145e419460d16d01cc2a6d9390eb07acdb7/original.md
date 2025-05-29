```
Connectivity{X,P}
```

Connectivity for a `Pxest` which holds the mesh information for the roots of `Pxest` quadtrees or octrees. The parameter `X` is 4 if the roots are quads (2D aka p4est) and 8 if they are hexes (3D aka p8est).

# Fields

  * `pointer`: The pointer (of type `P`) can be a pointer to either a `P4estTypes.P4est.p4est_connectivity` or a `P4estTypes.P4est.p8est_connectivity`.  See the help documentation for these types for more information about the underlying p4est structures.

# Usage

```
Connectivity{4}(name::Symbol)
```

Construct a connectivity mesh for the roots of a forest-of-quadtrees using p4est's built-in mesh connectivities.  Valid values for `name` are

  * `:unitsquare`: the unit square.
  * `:periodic`: all-periodic unit square.
  * `:rotwrap`: periodic unit square (the left and right faces are identified, and bottom and top opposite).
  * `:corner`: three-tree mesh around a corner.
  * `:pillow`: two trees on top of each other.
  * `:moebius`: a five-tree moebius band.
  * `:star`: six-tree star.
  * `:cubed`: six sides of a unit cube.
  * `:disk_nonperiodic`: five-tree flat spherical disk.
  * `:icosahedron`: for mapping the sphere using an icosahedron (see `@doc P4estTypes.P4est.p4est_connectivity_new_icosahedron` for more info).
  * `:shell2d`: 2D spherical shell.
  * `:disk2d`: maps a 2D disk.

---

```
Connectivity{4}(:disk, periodic_x::Bool, periodic_y::Bool)
```

Create a connectivity structure for a five-tree flat spherical disk.  The arguments `periodic_x` and `periodic_y` determine if the disk is periodic in the x and y directions, respectively.

See `@doc P4estTypes.P4est.p4est_connectivity_new_disk` for detailed information.

---

```
Connectivity{8}(name::Symbol)
```

Construct a connectivity mesh for the roots of a forest-of-octrees using p8est's built-in mesh connectivities.  Valid values for `name` are

  * `:unitcube`: the unit cube.
  * `:periodic`: an all-periodic unit cube.
  * `:rotcubes`: contains a few cubes (these are rotated against each other to stress the topology routines).
  * `:rotwrap`: a mostly periodic unit cube (see `@doc P4estTypes.P4est.p8est_connectivity_new_rotwrap`).
  * `:shell`: a spherical shell (see `@doc P4estTypes.P4est.p8est_connectivity_new_shell`).
  * `:sphere`: a solid sphere (see `@doc P4estTypes.P4est.p8est_connectivity_new_sphere`).
  * `:twocubes`: two cubes.
  * `:twowrap`: two cubes where the two far ends are identified periodically.

---

```
Connectivity{8}(:torus, nsegments)
```

Create a connectivity structure that builds a revolution torus.  Here `nsegments` are the number of trees along the great circle.

See `@doc P4estTypes.P4est.p8est_connectivity_new_torus` for detailed information.

---

```
Connectivity{8}(:torus, nsegments)
```

Create a connectivity structure that builds a revolution torus.  Here `nsegments` are the number of trees along the great circle.

See `@doc P4estTypes.P4est.p8est_connectivity_new_torus` for detailed information.

---

```
Connectivity{X}(:twotrees, l_face, r_face, orientation) where {X}
```

Create a connectivity structure (`X=4` for quadtrees and `X=8` for octrees) for two trees being rotated with respect to each other in a user-defined way.  Here `l_face` and `r_face` are the 0-based indices of left and right faces, respectively. The argument `orientation` gives the orientation code of the trees with respect to each other.

---

```
Connectivity{X}(vertices, elements) where {X}
```

Creates a connectivity from the given list of vertices and element-to-vertex connectivity.  The parameter set to `X=4` is for quads and `X=8` for hexes.

  * `vertices`: should be a number-of-vertices by 3 matrix where the columns correspond to x, y, and z coordinates (typically the `z` coordinate will be zero for a 2D forest).
  * `elements`: should be a number-of-vertices by 4 or 8 matrix where the columns vertex indices used to define each element. Note that z-ordering should be used, and it should use zero-indexing.

---

```
Connectivity{X}(filename::String) where {X}
```

Create a connectivity from an ABAQUS input at `filename`. The parameter set to `X=4` is for quads and `X=8` for hexes.

See `@doc P4estTypes.P4est.p4est_connectivity_read_inp` and `@doc P4estTypes.P4est.p8est_connectivity_read_inp` for example ABAQUS input files.

# See also

  * [`brick`](@ref): a function to create a rectangular [`Connectivity`](@ref).
  * [`connectivity`](@ref): a function to get the connectivity of a [`Pxest`](@ref).
  * [`refine`](@ref): a function to create a refined [`Connectivity`](@ref).
