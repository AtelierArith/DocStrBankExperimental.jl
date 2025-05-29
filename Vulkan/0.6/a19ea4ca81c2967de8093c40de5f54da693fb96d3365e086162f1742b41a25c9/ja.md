引数:

  * `name::String`
  * `instance::Instance`: デフォルトは `C_NULL`

[API ドキュメント](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/vkGetInstanceProcAddr.html)

```julia
_get_instance_proc_addr(
    name::AbstractString;
    instance
) -> Ptr{Nothing}

```
