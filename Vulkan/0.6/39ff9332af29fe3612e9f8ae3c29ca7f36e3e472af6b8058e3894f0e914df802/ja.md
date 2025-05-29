拡張: VK*EXT*vertex*input*dynamic_state

引数:

  * `vertex_input_dynamic_state::Bool`
  * `next::Ptr{Cvoid}`: デフォルトは `C_NULL`

[API ドキュメント](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkPhysicalDeviceVertexInputDynamicStateFeaturesEXT.html)

```julia
_PhysicalDeviceVertexInputDynamicStateFeaturesEXT(
    vertex_input_dynamic_state::Bool;
    next
) -> Vulkan._PhysicalDeviceVertexInputDynamicStateFeaturesEXT

```
