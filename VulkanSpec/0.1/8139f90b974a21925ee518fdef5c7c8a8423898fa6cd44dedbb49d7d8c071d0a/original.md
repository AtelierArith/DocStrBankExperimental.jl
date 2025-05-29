Function type classification.

Types:

  * `FTYPE_CREATE`: constructor (functions that begin with `vkCreate`).
  * `FTYPE_DESTROY`: destructor (functions that begin with `vkDestroy`).
  * `FTYPE_ALLOCATE`: allocator (functions that begin with `vkAllocate`).
  * `FTYPE_FREE`: deallocator (functions that begin with `vkFree`).
  * `FTYPE_COMMAND`: Vulkan command (functions that begin with `vkCmd`).
  * `FTYPE_QUERY`: used to query parameters, returned directly or indirectly through pointer mutation (typically, functions that begin with `vkEnumerate` and `vkGet`, but not all of them and possibly others).
  * `FTYPE_OTHER`: no identified type.

```julia
primitive type FunctionType <: Enum{Int32} 32
```
