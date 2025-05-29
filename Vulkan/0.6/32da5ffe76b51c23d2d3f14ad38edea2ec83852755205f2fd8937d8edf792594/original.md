Extension: VK_AMD_display_native_hdr

Arguments:

  * `local_dimming_enable::Bool`
  * `next::Ptr{Cvoid}`: defaults to `C_NULL`

[API documentation](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkSwapchainDisplayNativeHdrCreateInfoAMD.html)

```julia
_SwapchainDisplayNativeHdrCreateInfoAMD(
    local_dimming_enable::Bool;
    next
) -> Vulkan._SwapchainDisplayNativeHdrCreateInfoAMD

```
