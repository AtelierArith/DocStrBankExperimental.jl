```
GenerateBodyGrid(bd::BodyDyn; np=101)
```

Given BodyDyn structure, where each body only consists of several verts(usually 4 for quadrilateral and 3 for triangle), return the verts position of given number of points np in inertial frame by interpolation, of all bodies in the system.
