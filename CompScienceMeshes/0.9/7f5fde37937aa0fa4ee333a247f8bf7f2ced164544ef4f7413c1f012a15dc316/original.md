```
tetmeshcuboid(length::F, breadth::F, width::F, edge length::F) where F
```

returns Mesh(vertices, faces)

Function returns a simplicial volumetric mesh of a cuboid. It takes kwarg -  generator  :compsciencemeshes - is default, and gives a structured tetrahedral mesh of      a cuboid, the dimensions of the cuboid are approximated by multiples      of edge length -

```
there are 24 tetrahedrons in each unit cube - 4 on each facet - 
and there are n*m*p unit cubes in each cuboid, where n, m, p are number of
segments along length, breadth, width respectively.
```

:gmsh - returns a tetrahedral mesh of a cuboid using gmsh. 

Also see the gmsh function - tetgmshcuboid.
