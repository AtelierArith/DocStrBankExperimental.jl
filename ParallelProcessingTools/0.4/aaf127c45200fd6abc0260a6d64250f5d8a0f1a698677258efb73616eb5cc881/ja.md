```
@always_everywhere(expr)
```

現在のすべてのJuliaプロセスで`expr`を実行しますが、[`ensure_procinit()`](@ref)を使用して管理される場合、将来のすべてのJuliaプロセスでも実行されます。

`Distributed.everywhere`に似ていますが、`expr`を保存するため、`ensure_procinit`が将来のワーカープロセスでそれを実行できるようにします。

例:

```julia
@always_everywhere begin
    using SomePackage
    using SomeOtherPackage
    
    some_global_variable = 42
end
```

他にも[`ParallelProcessingTools.add_procinit_code`](@ref)や[`ParallelProcessingTools.ensure_procinit`](@ref)を参照してください。
