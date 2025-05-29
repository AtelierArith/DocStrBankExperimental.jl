拡張: VK*EXT*primitives*generated*query

引数:

  * `primitives_generated_query::Bool`
  * `primitives_generated_query_with_rasterizer_discard::Bool`
  * `primitives_generated_query_with_non_zero_streams::Bool`
  * `next::Any`: デフォルトは `C_NULL`

[API ドキュメント](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkPhysicalDevicePrimitivesGeneratedQueryFeaturesEXT.html)

```julia
PhysicalDevicePrimitivesGeneratedQueryFeaturesEXT(
    primitives_generated_query::Bool,
    primitives_generated_query_with_rasterizer_discard::Bool,
    primitives_generated_query_with_non_zero_streams::Bool;
    next
) -> Vulkan.PhysicalDevicePrimitivesGeneratedQueryFeaturesEXT

```
