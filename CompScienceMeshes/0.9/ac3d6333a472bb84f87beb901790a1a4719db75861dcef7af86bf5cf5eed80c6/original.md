```
meshrectangle(len::F, breadth::F, edge_length::F, udim = 3) where F
```

returns Mesh(vertices, faces)

Function calls arg - udim or universal dimension -     2 - returns a rectangle in a 2D space     3 - is default, returns a rectangle with the 3D coordinate system at z = 0

Function also calls a kwarg - generator -  :compsciencemeshes - is default, is pre-allocated with its vectors      of nodes and faces. It is a structured mesh. 

```
Nodes:
(m+1) nodes along b
(n+1) nodes along a
= (m+1)*(n+1) total nodes

Faces:
m elements along b 
n elements along a 
= 2*m*n total faces -> 2 triangles in each rectangular face

The faces along y-axis can be obtained by (2*element number) and 
(2*element number - 1), this is repeated for each element in x-axis.

The odd faces are the triangles right-angled at bottom,
  /|
 /_|      or laterally-inverted

 the even at top
  _      
 | /    
 |/        or laterally-inverted
```

:gmsh - returns an unstructured mesh using gmsh, which in turn using  Delaunay triangulation. 

kwarg (not implemented yet): boundary_only - returns the mesh of the boundary  of the rectangle, if true

Also see gmsh function - gmshrectangle.
