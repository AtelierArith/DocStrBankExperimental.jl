Register a user-defined callback and return the corresponding messenger. All the levels from `min_severity` will be included. Note that this controls only what messages are sent to the callback. The logging function may use logging macros such as `@info` or `@error` to easily filter logs through the Julia logging system.

A default function [`default_debug_callback`](@ref) can be converted to a function pointer to use as a callback.

!!! warning
    `callback` must be a function pointer of type `Ptr{Nothing}` obtained from a `callback_f` function as follows:   `callback = @cfunction(callback_f, UInt32, (DebugUtilsMessageSeverityFlagEXT, DebugUtilsMessageTypeFlagEXT, Ptr{VkCore.VkDebugUtilsMessengerCallbackDataEXT}, Ptr{Cvoid}))` with `callback_f` a Julia function with a signature matching the `@cfunction` call.


```julia
DebugUtilsMessengerEXT(
    instance::Vulkan.Instance,
    callback::Ptr{Nothing};
    min_severity,
    types
) -> Vulkan.DebugUtilsMessengerEXT

```
