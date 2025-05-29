Extension: VK_KHR_shared_presentable_image

Arguments:

  * `next::Ptr{Cvoid}`: defaults to `C_NULL`
  * `shared_present_supported_usage_flags::ImageUsageFlag`: defaults to `0`

[API documentation](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkSharedPresentSurfaceCapabilitiesKHR.html)

```julia
_SharedPresentSurfaceCapabilitiesKHR(
;
    next,
    shared_present_supported_usage_flags
) -> Vulkan._SharedPresentSurfaceCapabilitiesKHR

```
