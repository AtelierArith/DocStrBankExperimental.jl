拡張: VK*EXT*validation_cache

戻り値コード:

  * `SUCCESS`
  * `ERROR_OUT_OF_HOST_MEMORY`
  * `ERROR_OUT_OF_DEVICE_MEMORY`

引数:

  * `device::Device`
  * `validation_cache::ValidationCacheEXT`

!!! 警告     この関数が返すポインタは、Juliaが所有するメモリを保持しています。したがって、使用後にそれを解放するのは**あなたの**責任です（例: `Libc.free`を使用して）。

[API ドキュメント](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/vkGetValidationCacheDataEXT.html)

```julia
get_validation_cache_data_ext(
    device,
    validation_cache
) -> ResultTypes.Result{Tuple{UInt64, Ptr{Nothing}}, Vulkan.VulkanError}

```
