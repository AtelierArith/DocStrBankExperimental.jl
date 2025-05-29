拡張: VK*NV*optical_flow

引数:

  * `id::UInt32`
  * `size::UInt32`
  * `private_data::Ptr{Cvoid}`
  * `next::Any`: デフォルトは `C_NULL`

[API ドキュメント](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkOpticalFlowSessionCreatePrivateDataInfoNV.html)

```julia
OpticalFlowSessionCreatePrivateDataInfoNV(
    id::Integer,
    size::Integer,
    private_data::Ptr{Nothing};
    next
) -> Vulkan.OpticalFlowSessionCreatePrivateDataInfoNV

```
