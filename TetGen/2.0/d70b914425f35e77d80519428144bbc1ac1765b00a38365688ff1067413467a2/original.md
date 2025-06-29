```julia
tetrahedralize(
    input::TetGen.RawTetGenIO{Float64},
    flags::String
) -> TetGen.RawTetGenIO{Float64}

```

Tetrahedralize input.

```
  flags: -pYrq_Aa_miO_S_T_XMwcdzfenvgkJBNEFICQVh 
    -p  Tetrahedralizes a piecewise linear complex (PLC).
    -Y  Preserves the input surface mesh (does not modify it).
    -r  Reconstructs a previously generated mesh.
    -q  Refines mesh (to improve mesh quality).
    -R  Mesh coarsening (to reduce the mesh elements).
    -A  Assigns attributes to tetrahedra in different regions.
    -a  Applies a maximum tetrahedron volume constraint.
    -m  Applies a mesh sizing function.
    -i  Inserts a list of additional points.
    -O  Specifies the level of mesh optimization.
    -S  Specifies maximum number of added points.
    -T  Sets a tolerance for coplanar test (default 1e-8).
    -X  Suppresses use of exact arithmetic.
    -M  No merge of coplanar facets or very close vertices.
    -w  Generates weighted Delaunay (regular) triangulation.
    -c  Retains the convex hull of the PLC.
    -d  Detects self-intersections of facets of the PLC.
    -z  Numbers all output items starting from zero.
    -f  Outputs all faces to .face file.
    -e  Outputs all edges to .edge file.
    -n  Outputs tetrahedra neighbors to .neigh file.
    -v  Outputs Voronoi diagram to files.
    -g  Outputs mesh to .mesh file for viewing by Medit.
    -k  Outputs mesh to .vtk file for viewing by Paraview.
    -J  No jettison of unused vertices from output .node file.
    -B  Suppresses output of boundary information.
    -N  Suppresses output of .node file.
    -E  Suppresses output of .ele file.
    -F  Suppresses output of .face and .edge file.
    -I  Suppresses mesh iteration numbers.
    -C  Checks the consistency of the final mesh.
    -Q  Quiet:  No terminal output except errors.
    -V  Verbose:  Detailed information, more terminal output.
    -h  Help:  A brief instruction for using TetGen.
```
