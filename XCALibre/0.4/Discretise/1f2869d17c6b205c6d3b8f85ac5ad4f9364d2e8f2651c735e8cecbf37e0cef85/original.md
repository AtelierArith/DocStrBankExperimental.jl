```
construct_periodic(mesh, backend, patch1::Symbol, patch2::Symbol)
```

Function for construction of periodic boundary conditions.

### Input

  * `mesh` – Mesh.
  * `backend`  – Backend configuraton.
  * `patch1`  – Primary periodic patch ID.
  * `patch2`   – Neighbour periodic patch ID.

### Output

  * periodic::Tuple - tuple containing boundary defintions for `patch1` and `patch2` i.e. (periodic1, periodic2). The fields of `periodic1` and `periodic2` are 

      * `ID` – Index to access boundary information in mesh object
      * `value` – represents a `NamedTuple` with the following keyword arguments:

          * index – ID used to find boundary geometry information in the mesh object
          * distance – perpendicular distance between the patches
          * face_map – vector providing indeces to faces of match patch
          * ismaster – flat to identify one of the patch pairs as the main patch

### Example

```
- `periodic = construct_periodic(mesh, CPU(), :top, :bottom)` - Example using CPU 
backend with periodic boundaries named `top` and `bottom`.
```
