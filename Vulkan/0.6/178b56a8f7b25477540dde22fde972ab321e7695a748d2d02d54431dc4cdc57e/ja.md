引数:

  * `wait_semaphores::Vector{Semaphore}`
  * `buffer_binds::Vector{SparseBufferMemoryBindInfo}`
  * `image_opaque_binds::Vector{SparseImageOpaqueMemoryBindInfo}`
  * `image_binds::Vector{SparseImageMemoryBindInfo}`
  * `signal_semaphores::Vector{Semaphore}`
  * `next::Any`: デフォルトは `C_NULL`

[API ドキュメント](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkBindSparseInfo.html)

```julia
BindSparseInfo(
    wait_semaphores::AbstractArray,
    buffer_binds::AbstractArray,
    image_opaque_binds::AbstractArray,
    image_binds::AbstractArray,
    signal_semaphores::AbstractArray;
    next
) -> Vulkan.BindSparseInfo

```
