High-level wrapper for VkSamplerCreateInfo.

[API documentation](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkSamplerCreateInfo.html)

```julia
struct SamplerCreateInfo <: Vulkan.HighLevelStruct
```

  * `next::Any`
  * `flags::Vulkan.SamplerCreateFlag`
  * `mag_filter::Vulkan.Filter`
  * `min_filter::Vulkan.Filter`
  * `mipmap_mode::Vulkan.SamplerMipmapMode`
  * `address_mode_u::Vulkan.SamplerAddressMode`
  * `address_mode_v::Vulkan.SamplerAddressMode`
  * `address_mode_w::Vulkan.SamplerAddressMode`
  * `mip_lod_bias::Float32`
  * `anisotropy_enable::Bool`
  * `max_anisotropy::Float32`
  * `compare_enable::Bool`
  * `compare_op::Vulkan.CompareOp`
  * `min_lod::Float32`
  * `max_lod::Float32`
  * `border_color::Vulkan.BorderColor`
  * `unnormalized_coordinates::Bool`
