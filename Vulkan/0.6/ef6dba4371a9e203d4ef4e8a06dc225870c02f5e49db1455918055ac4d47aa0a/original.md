Extension: VK_NVX_binary_import

Arguments:

  * `_function::CuFunctionNVX`
  * `grid_dim_x::UInt32`
  * `grid_dim_y::UInt32`
  * `grid_dim_z::UInt32`
  * `block_dim_x::UInt32`
  * `block_dim_y::UInt32`
  * `block_dim_z::UInt32`
  * `shared_mem_bytes::UInt32`
  * `next::Ptr{Cvoid}`: defaults to `C_NULL`

[API documentation](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkCuLaunchInfoNVX.html)

```julia
_CuLaunchInfoNVX(
    _function,
    grid_dim_x::Integer,
    grid_dim_y::Integer,
    grid_dim_z::Integer,
    block_dim_x::Integer,
    block_dim_y::Integer,
    block_dim_z::Integer,
    shared_mem_bytes::Integer;
    next
)

```
