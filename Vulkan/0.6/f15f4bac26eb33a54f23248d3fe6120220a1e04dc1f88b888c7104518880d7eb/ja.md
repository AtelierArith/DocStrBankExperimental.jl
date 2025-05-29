拡張: VK*EXT*primitives*generated*query

引数:

  * `primitives_generated_query::Bool`
  * `primitives_generated_query_with_rasterizer_discard::Bool`
  * `primitives_generated_query_with_non_zero_streams::Bool`
  * `next::Ptr{Cvoid}`: デフォルトは `C_NULL`

[API ドキュメント](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkPhysicalDevicePrimitivesGeneratedQueryFeaturesEXT.html)

```julia
_PhysicalDevicePrimitivesGeneratedQueryFeaturesEXT(
    primitives_generated_query::Bool,
    primitives_generated_query_with_rasterizer_discard::Bool,
    primitives_generated_query_with_non_zero_streams::Bool;
    next
) -> Vulkan._PhysicalDevicePrimitivesGeneratedQueryFeaturesEXT

```
