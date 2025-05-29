```
meshcuboid(length::F, breadth::F, width::F, edge length::F) where F
```

returns Mesh(vertices, faces)

Function returns a simplicial areal mesh of a cuboid. It takes kwarg - generator  :compsciencemeshes - is default, and gives a structured mesh of      a cuboid, the dimensions of the cuboid are approximated by multiples      of edge length -

```
Number of faces = 2*(2*m*n) + 2*(2*n*p) + 2*(2*m*p) -> front, back; top, bottom;
left, right
where m is the number of elements along y, n along x, p along z

The odd faces are the triangles right-angled at bottom,
  /|
 /_|      or laterally-inverted

 the even at top
  _      
 | /    
 |/        or laterally-inverted

Number of vertices is 2*(n + 1)*(m + 1) + 2*(m + 1)*(p - 1) + 2*(n - 1)*(p - 1)
to avoid repeating the number of nodes along the edges of the cuboid; 
all nodes along front and back are stacked, 
then the nodes along the left and right, skipping the nodes along the left-front, 
left-back, right-front and right-back
then the nodes along the top and bottom, skipping the nodes along the top-front, 
-back, -left, -right, and bottom-front, -back, -left, -right.

Since, it is a hollow cuboidal mesh,
the nodes are numbered all along the front and back faces, first, and then, 
along the x-y edges in z - direction, like so

                             20----- 23----- 26
                             |       |       |
                             19      22      25
back =>                      |       |       |
                             18----- 21----- 24


                             12----- 14----- 17
middle                       |               |
layers =>                    11      .       16
                             |               |
                             10----- 13----- 15


                             3 ----- 6 ----- 9
                             |       |       |
                             2       5       8
front =>                     |       |       |
                             1 ----- 4 ----- 7
```

:gmsh - returns a areal mesh of a cuboid using gmsh and Closed Box only.

For other physical configurations of the surface of the cube, see gmshcuboid function.
