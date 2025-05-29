```
meshicosphere(;nu::Int = 1, r::F = 1.0, nr_verts) where F
```

returns Mesh(vertices, faces)

Function gives a geodesic icosahedron with subdivision frequency nu. Frequency nu = 1 returns regular unit icosahedron, and nu>1 preformes subdivision.  The result is a structured sphere.

Using subdivision frequency, possible number of vertices grows with nu as     [12+10*(nu+1)*(nu-1) for nu in range(1,33)]     which gives      [12, 42, 92, 162, 252, 362, 492, 642, 812, 1002, 1212, 1442, 1692, 1962,       2252, 2562, 2892, 3242, 3612, 4002, 4412, 4842, 5292, 5762, 6252, 6762,       7292, 7842, 8412, 9002, 9612, 10242]

For example, nu = 3, divides each triangle of the polygon of icosahedron to

```
                .
               / \
              .---.
             /\ / \
            .---.---.
           /\ /\ / \
          .---.---.---.
```

kwargs: Radius - is scaled with respect to the unit icosphere from given nu.  nr*verts - If nr*verts is given, nu will be adjusted such that icosphere contains at least nr_verts vertices.  

Original author and python code by vand@dtu.dk, 2014, 2017, 2021. Developed  in connection with https://ieeexplore.ieee.org/document/7182720
