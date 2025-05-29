```julia
triangulate(
    switches::String,
    tri_in::Triangulate.TriangulateIO
) -> Tuple{Triangulate.TriangulateIO, Triangulate.TriangulateIO}

```

Create triangulation. Returns tuple `(out::TriangulateIO, vor_out::TriangulateIO)` containing the output triangulation and the optional Voronoi tessellation.

After a call to triangulate(), the valid fields of `out` and `vorout` will depend, in an obvious way, on the choice of switches used.  Note that when the 'p' switch is used, the pointers `holelist` and `regionlist` are copied from `tri_in` to the output, but no new space is allocated;  On   the other hand, Triangle will never copy the `pointlist` pointer (or any  others); new space is allocated for `out.pointlist`, or if the 'N' switch is used, `out.pointlist` remains uninitialized. 

This is the list of switches used by triangle:

| Switch | Meaning                                                       |
| ------:|:------------------------------------------------------------- |
|     -p | Triangulates a Planar Straight Line Graph (.poly file).       |
|     -r | Refines a previously generated mesh.                          |
|     -q | Quality mesh generation.  A minimum angle may be specified.   |
|     -a | Applies a maximum triangle area constraint.                   |
|     -u | Applies a user-defined triangle constraint.                   |
|     -A | Applies attributes to identify triangles in certain regions.  |
|     -c | Encloses the convex hull with segments.                       |
|     -D | Conforming Delaunay:  all triangles are truly Delaunay.       |
|     -j | Jettison unused vertices from output .node file.              |
|     -e | Generates an edge list.                                       |
|     -v | Generates a Voronoi diagram.                                  |
|     -n | Generates a list of triangle neighbors.                       |
|     -g | Generates an .off file for Geomview.                          |
|     -B | Suppresses output of boundary information.                    |
|     -P | Suppresses output of .poly file.                              |
|     -N | Suppresses output of .node file.                              |
|     -E | Suppresses output of .ele file.                               |
|     -I | Suppresses mesh iteration numbers.                            |
|     -O | Ignores holes in .poly file.                                  |
|     -X | Suppresses use of exact arithmetic.                           |
|     -z | Numbers all items starting from zero (rather than one).       |
|    -o2 | Generates second-order subparametric elements.                |
|     -Y | Suppresses boundary segment splitting.                        |
|     -S | Specifies maximum number of added Steiner points.             |
|     -i | Uses incremental method, rather than divide-and-conquer.      |
|     -F | Uses Fortune's sweepline algorithm, rather than d-and-c.      |
|     -l | Uses vertical cuts only, rather than alternating cuts.        |
|     -s | Force segments into mesh by splitting (instead of using CDT). |
|     -C | Check consistency of final mesh.                              |
|     -Q | Quiet:  No terminal output except errors.                     |
|     -V | Verbose:  Detailed information on what I'm doing.             |
