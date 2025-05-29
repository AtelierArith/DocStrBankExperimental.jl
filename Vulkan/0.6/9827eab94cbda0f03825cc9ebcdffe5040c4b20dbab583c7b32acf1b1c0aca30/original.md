Extension: VK_NV_optical_flow

Arguments:

  * `regions::Vector{Rect2D}`
  * `next::Any`: defaults to `C_NULL`
  * `flags::OpticalFlowExecuteFlagNV`: defaults to `0`

[API documentation](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkOpticalFlowExecuteInfoNV.html)

```julia
OpticalFlowExecuteInfoNV(
    regions::AbstractArray;
    next,
    flags
) -> Vulkan.OpticalFlowExecuteInfoNV

```
