```julia
marching_tetrahedra(
    coord,
    cellnodes,
    func,
    planes,
    flevels;
    tol,
    primepoints,
    primevalues,
    Tv,
    Tp,
    Tf
)

```

Extract isosurfaces and plane interpolation for function on 3D tetrahedral mesh.

The basic observation is that locally on a tetrahedron, cuts with planes and isosurfaces of P1 functions look the same. This method calculates data for several plane cuts and several isosurfaces at once. 

Input parameters:

  * `coord`: 3 x n_points matrix of point coordinates
  * `cellnodes`: 4 x n_cells matrix of point numbers per tetrahedron
  * `func`: n_points vector of piecewise linear function values
  * `planes`: vector of plane equations `ax+by+cz+d=0`,each  stored as vector [a,b,c,d]
  * `flevels`: vector of function isolevels

Keyword arguments:

  * `tol`: tolerance for tet x plane intersection
  * `primepoints`:  3 x n_prime matrix of "corner points" of domain to be plotted. These are not in the mesh but are used to calculate the axis size e.g. by Makie
  * `primevalues`:  n_prime vector of function values in corner points. These can be used to calculate function limits e.g. by Makie
  * `Tv`:  type of function values returned
  * `Tp`:  type of points returned
  * `Tf`:  type of facets returned

Return values: (points, tris, values)

  * `points`: vector of points (Tp)
  * `tris`: vector of triangles (Tf)
  * `values`: vector of function values (Tv)

These can be readily turned into a mesh with function values on it.

Caveat: points with similar coordinates are not identified, e.g. an intersection of a plane and an edge will generate as many edge intersection points as there are tetrahedra adjacent to that edge. As a consequence, normal calculations for visualization always will end up with facet normals, not point normals, and the visual impression of a rendered isosurface will show its piecewise linear genealogy.
