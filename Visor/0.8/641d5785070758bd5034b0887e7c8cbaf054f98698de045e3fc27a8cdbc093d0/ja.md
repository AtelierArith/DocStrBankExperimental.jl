```
process(id, fn;
        args=(),
        namedargs=(;),
        force_interrupt_after::Real=1.0,
        stop_waiting_after::Real=Inf,
        debounce_time=NaN,
        trace_exception=false,
        thread=true,
        restart=:transient)::ProcessSpec
```

強制的に中断される可能性のある監視タスクを宣言します。

`id` はプロセス名で、`fn` はタスク関数です。

`process` は仕様のみを返します：タスク関数は [`supervise`](@ref) で開始する必要があります。

詳細については、オンラインドキュメントの [`process`](@ref) を参照してください。
