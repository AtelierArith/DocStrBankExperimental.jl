Extension: VK_EXT_primitives_generated_query

Arguments:

  * `primitives_generated_query::Bool`
  * `primitives_generated_query_with_rasterizer_discard::Bool`
  * `primitives_generated_query_with_non_zero_streams::Bool`
  * `next::Any`: defaults to `C_NULL`

[API documentation](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkPhysicalDevicePrimitivesGeneratedQueryFeaturesEXT.html)

```julia
PhysicalDevicePrimitivesGeneratedQueryFeaturesEXT(
    primitives_generated_query::Bool,
    primitives_generated_query_with_rasterizer_discard::Bool,
    primitives_generated_query_with_non_zero_streams::Bool;
    next
) -> Vulkan.PhysicalDevicePrimitivesGeneratedQueryFeaturesEXT

```
