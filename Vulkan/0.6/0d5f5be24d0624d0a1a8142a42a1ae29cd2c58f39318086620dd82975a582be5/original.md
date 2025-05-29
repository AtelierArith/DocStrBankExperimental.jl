Extension: VK_NV_optical_flow

Arguments:

  * `id::UInt32`
  * `size::UInt32`
  * `private_data::Ptr{Cvoid}`
  * `next::Ptr{Cvoid}`: defaults to `C_NULL`

[API documentation](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkOpticalFlowSessionCreatePrivateDataInfoNV.html)

```julia
_OpticalFlowSessionCreatePrivateDataInfoNV(
    id::Integer,
    size::Integer,
    private_data::Ptr{Nothing};
    next
) -> Vulkan._OpticalFlowSessionCreatePrivateDataInfoNV

```
