```julia
copy_subcomponent_time_series!(
    subsystem::PowerSystems.StaticInjectionSubsystem,
    subcomponent::PowerSystems.Component
)

```

サブコンポーネントのすべての時系列データを、基になる参照をコピーすることによってサブシステムに効率的に追加します。
