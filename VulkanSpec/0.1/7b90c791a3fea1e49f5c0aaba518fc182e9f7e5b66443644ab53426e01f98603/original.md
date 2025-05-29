Return whether an extension is enabled for standard Vulkan - that is, a given symbol `x` is either core or is from an extension that has not been disabled, or is not exclusive to Vulkan SC.

```julia
isenabled(x, extensions::VulkanSpec.Extensions) -> Any

```
