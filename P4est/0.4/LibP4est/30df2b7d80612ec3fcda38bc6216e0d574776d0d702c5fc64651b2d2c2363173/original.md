```
p8est_connectivity_read_inp(filename)
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
     1,    5,   -5,    5
     2,    5,    5,    5
     3,    5,    0,    5
     4,   -5,    5,    5
     5,    0,    5,    5
     6,   -5,   -5,    5
     7,   -5,    0,    5
     8,    0,   -5,    5
     9,    0,    0,    5
    10,    5,    5,   -5
    11,    5,   -5,   -5
    12,    5,    0,   -5
    13,   -5,   -5,   -5
    14,    0,   -5,   -5
    15,   -5,    5,   -5
    16,   -5,    0,   -5
    17,    0,    5,   -5
    18,    0,    0,   -5
    19,   -5,   -5,    0
    20,    5,   -5,    0
    21,    0,   -5,    0
    22,   -5,    5,    0
    23,   -5,    0,    0
    24,    5,    5,    0
    25,    0,    5,    0
    26,    5,    0,    0
    27,    0,    0,    0
 *Element, type=C3D8, ELSET=EB1
     1,       6,      19,      23,       7,       8,      21,      27,       9
     2,      19,      13,      16,      23,      21,      14,      18,      27
     3,       7,      23,      22,       4,       9,      27,      25,       5
     4,      23,      16,      15,      22,      27,      18,      17,      25
     5,       8,      21,      27,       9,       1,      20,      26,       3
     6,      21,      14,      18,      27,      20,      11,      12,      26
     7,       9,      27,      25,       5,       3,      26,      24,       2
     8,      27,      18,      17,      25,      26,      12,      10,      24
```

This function reads a mesh from *filename* and returns an associated `p4est` connectivity.

### Parameters

  * `filename`:[in] file to read the connectivity from

### Returns

an allocated connectivity associated with the mesh in *filename*

### Prototype

```c
p8est_connectivity_t *p8est_connectivity_read_inp (const char *filename);
```
