引数:

  * `device::Device`
  * `sampler::Sampler` (externsync)
  * `allocator::AllocationCallbacks`: デフォルトは `C_NULL`

[API ドキュメント](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/vkDestroySampler.html)

```julia
destroy_sampler(device, sampler; allocator)

```
