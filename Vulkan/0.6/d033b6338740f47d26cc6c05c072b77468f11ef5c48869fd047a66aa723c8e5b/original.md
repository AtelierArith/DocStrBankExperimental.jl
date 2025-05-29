Extension: VK_NV_dedicated_allocation

Arguments:

  * `dedicated_allocation::Bool`
  * `next::Ptr{Cvoid}`: defaults to `C_NULL`

[API documentation](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkDedicatedAllocationImageCreateInfoNV.html)

```julia
_DedicatedAllocationImageCreateInfoNV(
    dedicated_allocation::Bool;
    next
) -> Vulkan._DedicatedAllocationImageCreateInfoNV

```
