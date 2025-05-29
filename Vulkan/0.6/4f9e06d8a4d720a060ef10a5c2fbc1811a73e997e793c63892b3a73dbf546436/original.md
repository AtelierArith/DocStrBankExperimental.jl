Extension: VK_LUNARG_direct_driver_loading

Arguments:

  * `mode::DirectDriverLoadingModeLUNARG`
  * `drivers::Vector{DirectDriverLoadingInfoLUNARG}`
  * `next::Any`: defaults to `C_NULL`

[API documentation](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkDirectDriverLoadingListLUNARG.html)

```julia
DirectDriverLoadingListLUNARG(
    mode::Vulkan.DirectDriverLoadingModeLUNARG,
    drivers::AbstractArray;
    next
) -> Vulkan.DirectDriverLoadingListLUNARG

```
