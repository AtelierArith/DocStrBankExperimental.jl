VkCuLaunchInfoNVXの高レベルラッパー。

拡張: VK*NVX*binary_import

[APIドキュメント](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkCuLaunchInfoNVX.html)

```julia
struct CuLaunchInfoNVX <: Vulkan.HighLevelStruct
```

  * `next::Any`
  * `_function::Vulkan.CuFunctionNVX`
  * `grid_dim_x::UInt32`
  * `grid_dim_y::UInt32`
  * `grid_dim_z::UInt32`
  * `block_dim_x::UInt32`
  * `block_dim_y::UInt32`
  * `block_dim_z::UInt32`
  * `shared_mem_bytes::UInt32`
