Convenience function for setting a specific driver used by Vulkan. Only SwiftShader is currently supported. To add another driver, you must specify it by hand. You can achieve that by setting the environment variable `VK_DRIVER_FILES` (formerly `VK_ICD_FILENAMES`) to point to your own driver JSON manifest file, as described in https://github.com/KhronosGroup/Vulkan-Loader/blob/main/docs/LoaderDriverInterface.md#driver-discovery.

Available drivers:

  * SwiftShader: a CPU implementation of Vulkan. Requires `SwiftShader_jll` to be imported in `mod`.

```julia
set_driver(backend::Symbol)

```
