```
cleanup(consume_ctx::AbstractConsumeContext, e::Exception)
```

このメソッドをオーバーライドすることで、カスタム例外処理を消費コンテキストで行うことができます。このメソッドは、`e`をさらに転送する`rethrow()`の直前に呼び出されます。

関連情報としては、[`consume!`](@ref)、[`setup_tasks!`](@ref)、[`task_done!`](@ref)、[`sync_tasks`](@ref)があります。
