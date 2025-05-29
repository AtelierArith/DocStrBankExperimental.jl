戻りコード:

  * `SUCCESS`
  * `ERROR_OUT_OF_HOST_MEMORY`
  * `ERROR_OUT_OF_DEVICE_MEMORY`
  * `ERROR_INVALID_OPAQUE_CAPTURE_ADDRESS_KHR`

引数:

  * `device::Device`
  * `mag_filter::Filter`
  * `min_filter::Filter`
  * `mipmap_mode::SamplerMipmapMode`
  * `address_mode_u::SamplerAddressMode`
  * `address_mode_v::SamplerAddressMode`
  * `address_mode_w::SamplerAddressMode`
  * `mip_lod_bias::Float32`
  * `anisotropy_enable::Bool`
  * `max_anisotropy::Float32`
  * `compare_enable::Bool`
  * `compare_op::CompareOp`
  * `min_lod::Float32`
  * `max_lod::Float32`
  * `border_color::BorderColor`
  * `unnormalized_coordinates::Bool`
  * `allocator::AllocationCallbacks`: デフォルトは `C_NULL`
  * `next::Any`: デフォルトは `C_NULL`
  * `flags::SamplerCreateFlag`: デフォルトは `0`

[API ドキュメント](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/vkCreateSampler.html)

```julia
create_sampler(
    device,
    mag_filter::Vulkan.Filter,
    min_filter::Vulkan.Filter,
    mipmap_mode::Vulkan.SamplerMipmapMode,
    address_mode_u::Vulkan.SamplerAddressMode,
    address_mode_v::Vulkan.SamplerAddressMode,
    address_mode_w::Vulkan.SamplerAddressMode,
    mip_lod_bias::Real,
    anisotropy_enable::Bool,
    max_anisotropy::Real,
    compare_enable::Bool,
    compare_op::Vulkan.CompareOp,
    min_lod::Real,
    max_lod::Real,
    border_color::Vulkan.BorderColor,
    unnormalized_coordinates::Bool;
    allocator,
    next,
    flags
) -> ResultTypes.Result{Vulkan.Sampler, Vulkan.VulkanError}

```
