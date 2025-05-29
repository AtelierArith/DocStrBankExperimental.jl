Extension: VK_AMD_display_native_hdr

Arguments:

  * `local_dimming_support::Bool`
  * `next::Ptr{Cvoid}`: defaults to `C_NULL`

[API documentation](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkDisplayNativeHdrSurfaceCapabilitiesAMD.html)

```julia
_DisplayNativeHdrSurfaceCapabilitiesAMD(
    local_dimming_support::Bool;
    next
) -> Vulkan._DisplayNativeHdrSurfaceCapabilitiesAMD

```
