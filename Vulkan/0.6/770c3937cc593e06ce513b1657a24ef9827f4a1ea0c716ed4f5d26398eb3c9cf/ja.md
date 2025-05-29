拡張: VK*KHR*acceleration_structure

引数:

  * `vertex_format::Format`
  * `vertex_data::DeviceOrHostAddressConstKHR`
  * `vertex_stride::UInt64`
  * `max_vertex::UInt32`
  * `index_type::IndexType`
  * `index_data::DeviceOrHostAddressConstKHR`
  * `transform_data::DeviceOrHostAddressConstKHR`
  * `next::Any`: デフォルトは `C_NULL`

[API ドキュメント](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkAccelerationStructureGeometryTrianglesDataKHR.html)

```julia
AccelerationStructureGeometryTrianglesDataKHR(
    vertex_format::Vulkan.Format,
    vertex_data::Vulkan.DeviceOrHostAddressConstKHR,
    vertex_stride::Integer,
    max_vertex::Integer,
    index_type::Vulkan.IndexType,
    index_data::Vulkan.DeviceOrHostAddressConstKHR,
    transform_data::Vulkan.DeviceOrHostAddressConstKHR;
    next
) -> Vulkan.AccelerationStructureGeometryTrianglesDataKHR

```
