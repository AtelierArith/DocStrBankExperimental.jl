拡張: VK*EXT*subpass*merge*feedback

引数:

  * `subpass_merge_feedback::Bool`
  * `next::Ptr{Cvoid}`: デフォルトは `C_NULL`

[API ドキュメント](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkPhysicalDeviceSubpassMergeFeedbackFeaturesEXT.html)

```julia
_PhysicalDeviceSubpassMergeFeedbackFeaturesEXT(
    subpass_merge_feedback::Bool;
    next
) -> Vulkan._PhysicalDeviceSubpassMergeFeedbackFeaturesEXT

```
