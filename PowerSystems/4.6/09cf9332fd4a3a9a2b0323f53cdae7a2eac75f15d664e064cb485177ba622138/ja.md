```julia
set_dynamic_injector!(
    static_injector::PowerSystems.StaticInjection,
    dynamic_injector::Union{Nothing, PowerSystems.DynamicInjection}
)

```

動的インジェクタをサポートしたい任意のStaticInjection構造体は、このメソッドを実装して値を設定する必要があります。

このメソッドは内部使用のためだけのものです。
