```julia
add_component!(
    sys::PowerSystems.System,
    dyn_injector::PowerSystems.DynamicInjection,
    static_injector::PowerSystems.StaticInjection;
    kwargs...
)

```

システムに動的インジェクタを追加します。

コンポーネントは1つの `System` にしか追加できません。名前が `static_injector` の名前と一致しない場合は ArgumentError をスローします。`static_injector` がシステムに接続されていない場合は ArgumentError をスローします。

一般的な `add_component!` メソッドのすべてのルールも適用されます。
