Arguments:

  * `name::String`
  * `instance::Instance`: defaults to `C_NULL`

[API documentation](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/vkGetInstanceProcAddr.html)

```julia
_get_instance_proc_addr(
    name::AbstractString;
    instance
) -> Ptr{Nothing}

```
