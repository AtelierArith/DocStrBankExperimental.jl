```
inside = isinside_closed_STL(mesh::Mesh, Pt, eps=1e-3)
```

Determine whether a point `Pt` is inside a 3D closed triangular `*.stl` surface or not.

This implements the winding number method, following the python code: https://github.com/marmakoide/inside-3d-mesh

This again is described in the following [paper](https://igl.ethz.ch/projects/winding-number/) by Alec Jacobson, Ladislav Kavan and Olga Sorkine-Hornung.
