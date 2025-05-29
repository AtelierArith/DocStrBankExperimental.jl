デフォルトのコールバックは、[`DebugUtilsMessengerEXT`](@ref)を使用してデバッグを行います。

```julia
default_debug_callback(
    message_severity,
    message_type,
    callback_data_ptr,
    user_data_ptr
) -> UInt32

```
