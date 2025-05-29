拡張: VK*KHR*deferred*host*operations

引数:

  * `device::Device`
  * `operation::DeferredOperationKHR` (externsync)
  * `allocator::AllocationCallbacks`: デフォルトは `C_NULL`

[API ドキュメント](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/vkDestroyDeferredOperationKHR.html)

```julia
destroy_deferred_operation_khr(device, operation; allocator)

```
