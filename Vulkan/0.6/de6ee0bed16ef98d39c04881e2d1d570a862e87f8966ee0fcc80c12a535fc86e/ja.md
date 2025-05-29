拡張: VK*NVX*binary_import

引数:

  * `_function::CuFunctionNVX`
  * `grid_dim_x::UInt32`
  * `grid_dim_y::UInt32`
  * `grid_dim_z::UInt32`
  * `block_dim_x::UInt32`
  * `block_dim_y::UInt32`
  * `block_dim_z::UInt32`
  * `shared_mem_bytes::UInt32`
  * `next::Any`: デフォルトは `C_NULL`

[API ドキュメント](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkCuLaunchInfoNVX.html)

```julia
CuLaunchInfoNVX(
    _function::Vulkan.CuFunctionNVX,
    grid_dim_x::Integer,
    grid_dim_y::Integer,
    grid_dim_z::Integer,
    block_dim_x::Integer,
    block_dim_y::Integer,
    block_dim_z::Integer,
    shared_mem_bytes::Integer;
    next
) -> Vulkan.CuLaunchInfoNVX

```
