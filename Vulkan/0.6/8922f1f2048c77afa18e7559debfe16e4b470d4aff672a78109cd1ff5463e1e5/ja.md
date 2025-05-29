拡張: VK*EXT*vertex*attribute*divisor

引数:

  * `vertex_attribute_instance_rate_divisor::Bool`
  * `vertex_attribute_instance_rate_zero_divisor::Bool`
  * `next::Any`: デフォルトは `C_NULL`

[API ドキュメント](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkPhysicalDeviceVertexAttributeDivisorFeaturesEXT.html)

```julia
PhysicalDeviceVertexAttributeDivisorFeaturesEXT(
    vertex_attribute_instance_rate_divisor::Bool,
    vertex_attribute_instance_rate_zero_divisor::Bool;
    next
) -> Vulkan.PhysicalDeviceVertexAttributeDivisorFeaturesEXT

```
