```
P4estMesh{NDIMS, NDIMS_AMBIENT} <: AbstractMesh{NDIMS}
```

An unstructured curved mesh based on trees that uses the C library `p4est` to manage trees and mesh refinement.

The parameter `NDIMS` denotes the dimension of the spatial domain or manifold represented by the mesh itself, while `NDIMS_AMBIENT` denotes the dimension of the ambient space in which the mesh is embedded. For example, the type `P4estMesh{3, 3}` corresponds to a standard mesh for a three-dimensional volume, whereas `P4estMesh{2, 3}` corresponds to a mesh for a two-dimensional surface or shell in three-dimensional space.

!!! warning "Experimental implementation"
    The use of `NDIMS != NDIMS_AMBIENT` is an experimental feature and may change in future releases.

