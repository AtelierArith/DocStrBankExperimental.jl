Extension: VK_EXT_vertex_attribute_divisor

Arguments:

  * `vertex_attribute_instance_rate_divisor::Bool`
  * `vertex_attribute_instance_rate_zero_divisor::Bool`
  * `next::Ptr{Cvoid}`: defaults to `C_NULL`

[API documentation](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkPhysicalDeviceVertexAttributeDivisorFeaturesEXT.html)

```julia
_PhysicalDeviceVertexAttributeDivisorFeaturesEXT(
    vertex_attribute_instance_rate_divisor::Bool,
    vertex_attribute_instance_rate_zero_divisor::Bool;
    next
) -> Vulkan._PhysicalDeviceVertexAttributeDivisorFeaturesEXT

```
