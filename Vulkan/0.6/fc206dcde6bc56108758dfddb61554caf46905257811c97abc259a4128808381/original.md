Arguments:

  * `wait_semaphores::Vector{Semaphore}`
  * `buffer_binds::Vector{_SparseBufferMemoryBindInfo}`
  * `image_opaque_binds::Vector{_SparseImageOpaqueMemoryBindInfo}`
  * `image_binds::Vector{_SparseImageMemoryBindInfo}`
  * `signal_semaphores::Vector{Semaphore}`
  * `next::Ptr{Cvoid}`: defaults to `C_NULL`

[API documentation](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkBindSparseInfo.html)

```julia
_BindSparseInfo(
    wait_semaphores::AbstractArray,
    buffer_binds::AbstractArray,
    image_opaque_binds::AbstractArray,
    image_binds::AbstractArray,
    signal_semaphores::AbstractArray;
    next
) -> Vulkan._BindSparseInfo

```
