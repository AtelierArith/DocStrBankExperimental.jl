VkMemoryGetRemoteAddressInfoNVの高レベルラッパー。

拡張: VK*NV*external*memory*rdma

[APIドキュメント](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkMemoryGetRemoteAddressInfoNV.html)

```julia
struct MemoryGetRemoteAddressInfoNV <: Vulkan.HighLevelStruct
```

  * `next::Any`
  * `memory::Vulkan.DeviceMemory`
  * `handle_type::Vulkan.ExternalMemoryHandleTypeFlag`
