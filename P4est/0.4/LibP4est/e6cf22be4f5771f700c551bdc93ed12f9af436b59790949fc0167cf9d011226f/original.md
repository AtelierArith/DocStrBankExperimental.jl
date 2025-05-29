```
p4est_connectivity_read_inp(filename)
```

Create a `p4est` connectivity from an ABAQUS input file.

This utility function reads a basic ABAQUS file supporting element type with the prefix C2D4, CPS4, and S4 in 2D and of type C3D8 reading them as bilinear quadrilateral and trilinear hexahedral trees respectively.

A basic 2D mesh is given below. The `*Node` section gives the vertex number and x, y, and z components for each vertex. The `*Element` section gives the 4 vertices in 2D (8 vertices in 3D) of each element in counter clockwise order. So in 2D the nodes are given as:

4 3 +–––––––––-+ | | | | | | | | | | | | +–––––––––-+ 1 2

and in 3D they are given as:

8 7 +––––––––––-+ |\ |\ | \ | \ | \ | \ | \ | \ | 5+––––––––––-+6 | | | | +––|––––––––+ | 4\ | 3 \ | \ | \ | \ | \ | \| \| +––––––––––-+ 1 2

```c++
 *Heading
  box.inp
 *Node
 1,  -5, -5, 0
 2,   5, -5, 0
 3,   5,  5, 0
 4,  -5,  5, 0
 5,   0, -5, 0
 6,   5,  0, 0
 7,   0,  5, 0
 8,  -5,  0, 0
 9,   1, -1, 0
 10,  0,  0, 0
 11, -2,  1, 0
 *Element, type=CPS4, ELSET=Surface1
 1,  1, 10, 11, 8
 2,  3, 10, 9,  6
 3,  9, 10, 1,  5
 4,  7,  4, 8, 11
 5, 11, 10, 3,  7
 6,  2,  6, 9,  5
```

This function reads a mesh from *filename* and returns an associated `p4est` connectivity.

### Parameters

  * `filename`:[in] file to read the connectivity from

### Returns

an allocated connectivity associated with the mesh in *filename* or NULL if an error occurred.

### Prototype

```c
p4est_connectivity_t *p4est_connectivity_read_inp (const char *filename);
```
