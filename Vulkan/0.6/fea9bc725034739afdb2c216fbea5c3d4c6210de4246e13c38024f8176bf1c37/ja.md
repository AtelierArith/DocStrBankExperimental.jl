ユーザー定義のコールバックを登録し、対応するメッセンジャーを返します。`min_severity` からのすべてのレベルが含まれます。これはコールバックに送信されるメッセージを制御するだけであることに注意してください。ロギング関数は、`@info` や `@error` などのロギングマクロを使用して、Julia ロギングシステムを通じてログを簡単にフィルタリングできます。

デフォルト関数 [`default_debug_callback`](@ref) は、コールバックとして使用するために関数ポインタに変換できます。

!!! 警告     `callback` は、次のように `callback_f` 関数から取得した `Ptr{Nothing}` 型の関数ポインタでなければなりません: `callback = @cfunction(callback_f, UInt32, (DebugUtilsMessageSeverityFlagEXT, DebugUtilsMessageTypeFlagEXT, Ptr{VkCore.VkDebugUtilsMessengerCallbackDataEXT}, Ptr{Cvoid}))` ここで、`callback_f` は `@cfunction` 呼び出しと一致するシグネチャを持つ Julia 関数です。

```julia
DebugUtilsMessengerEXT(
    instance::Vulkan.Instance,
    callback::Ptr{Nothing};
    min_severity,
    types
) -> Vulkan.DebugUtilsMessengerEXT

```
