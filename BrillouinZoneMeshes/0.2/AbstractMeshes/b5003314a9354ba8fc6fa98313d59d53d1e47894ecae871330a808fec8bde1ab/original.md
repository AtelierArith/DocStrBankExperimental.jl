```
module AbstractMeshes
```

This sub-module defines abstract type "AbstractMesh",  from which all concrete types of meshes in this package derive.  All functions expected by a sub-type of "AbstractMesh" are defined in this file,  including AbstractArray interface requirements and functions like "locate" and "volume". If the implementation of a function is type-specific,  the function defined in this file will return error.
