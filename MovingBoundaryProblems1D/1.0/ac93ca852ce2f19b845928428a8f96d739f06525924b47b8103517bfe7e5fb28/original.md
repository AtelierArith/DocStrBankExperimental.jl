```
MBGeometry{T}
```

Definition of the geometry for a moving boundary problem problem.

# Fields

  * `mesh_points::T`: The mesh points. Must be sorted and satisfy `mesh_points[begin] = 0` and `mesh_points[end] = 1` (if they do not satisfy this, they are scaled first).
  * `spacings::T`: The spacings between the mesh points.
  * `volumes::T`: The volumes of the cells defined by the mesh points.

# Constructors

To construct the geometry, you can directly call the default constructor, 

```
MBGeometry(mesh_points, spacings, volumes)
```

or you can call the convenience constructor,

```
MBGeometry(mesh_points)
```

which will compute the spacings and volumes for you.

See also [`MBProblem`](@ref).
