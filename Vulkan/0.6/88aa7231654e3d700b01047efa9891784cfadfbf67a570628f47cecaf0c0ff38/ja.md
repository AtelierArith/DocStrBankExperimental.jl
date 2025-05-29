引数:

  * `supported::Bool`
  * `next::Ptr{Cvoid}`: デフォルトは `C_NULL`

[API ドキュメント](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkDescriptorSetLayoutSupport.html)

```julia
_DescriptorSetLayoutSupport(
    supported::Bool;
    next
) -> Vulkan._DescriptorSetLayoutSupport

```
