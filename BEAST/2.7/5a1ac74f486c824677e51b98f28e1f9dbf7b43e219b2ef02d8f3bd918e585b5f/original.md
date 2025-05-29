```
duallagrangec0d1(originalmesh, refinedmesh)
```

It is the user responsibility to provide two meshes representing the same object. The second mesh needs to be obtained using "barycentric_refinement(originalmesh)". This basis function creats the dual Lagrange basis function and return an object that contains array of shapes [fns] It also return a gemoetry containing the refined mesh.
