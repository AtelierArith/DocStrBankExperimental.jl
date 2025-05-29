```
meshsphere(radius::F, h::F) where F
```

returns Mesh(vertices, faces)

Function gives a simplicial areal mesh of a sphere of radius and edge length. Additionally, the function takes kwargs - generator, delaunay -generator :compsciencemeshes - is default     -delaunay –- only a kwarg argument for compsciencemeshes     :(2D) - is default, the triangulation is a 2D delaunay and is significantly faster     than its 3D counterpart for medium to large meshes. The triangulation is done for     x- and y- vertices, and the z- coordinate of the vertices are calculated from x, y      using Stereographic projection.     :(3D) - calls the 3D Delaunay for triangulation, is significantly slower for      medium to large meshes. :gmsh - returns a mesh using gmsh

The delaunay kwarg is only an argument for compsciencemeshes. The generator kwarg  has precedence over delaunay.

Also see function - gmshsphere.
