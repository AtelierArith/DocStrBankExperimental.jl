Structure type classification.

Types:

  * `STYPE_CREATE_INFO`: holds constructor parameters (structures that end with `CreateInfo`).
  * `STYPE_ALLOCATE_INFO`: holds allocator parameters (structures that end with `AllocateInfo`).
  * `STYPE_GENERIC_INFO`: holds parameters for another function or structure (structures that end with `Info`, excluding those falling into the previous types).
  * `STYPE_DATA`: usually represents user or Vulkan data.
  * `STYPE_PROPERTY`: is a property returned by Vulkan in a `returnedonly` structure, usually done through `FTYPE_QUERY` type functions.

```julia
primitive type StructType <: Enum{Int32} 32
```
