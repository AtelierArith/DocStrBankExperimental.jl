Extension: VK_KHR_acceleration_structure

Arguments:

  * `vertex_format::Format`
  * `vertex_data::_DeviceOrHostAddressConstKHR`
  * `vertex_stride::UInt64`
  * `max_vertex::UInt32`
  * `index_type::IndexType`
  * `index_data::_DeviceOrHostAddressConstKHR`
  * `transform_data::_DeviceOrHostAddressConstKHR`
  * `next::Ptr{Cvoid}`: defaults to `C_NULL`

[API documentation](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkAccelerationStructureGeometryTrianglesDataKHR.html)

```julia
_AccelerationStructureGeometryTrianglesDataKHR(
    vertex_format::Vulkan.Format,
    vertex_data::Vulkan._DeviceOrHostAddressConstKHR,
    vertex_stride::Integer,
    max_vertex::Integer,
    index_type::Vulkan.IndexType,
    index_data::Vulkan._DeviceOrHostAddressConstKHR,
    transform_data::Vulkan._DeviceOrHostAddressConstKHR;
    next
) -> Vulkan._AccelerationStructureGeometryTrianglesDataKHR

```
