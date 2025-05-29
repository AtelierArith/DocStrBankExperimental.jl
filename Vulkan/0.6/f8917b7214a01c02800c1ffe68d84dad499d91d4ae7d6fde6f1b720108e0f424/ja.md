VkPhysicalDevice16BitStorageFeaturesの高レベルラッパー。

[APIドキュメント](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkPhysicalDevice16BitStorageFeatures.html)

```julia
struct PhysicalDevice16BitStorageFeatures <: Vulkan.HighLevelStruct
```

  * `next::Any`
  * `storage_buffer_16_bit_access::Bool`
  * `uniform_and_storage_buffer_16_bit_access::Bool`
  * `storage_push_constant_16::Bool`
  * `storage_input_output_16::Bool`
