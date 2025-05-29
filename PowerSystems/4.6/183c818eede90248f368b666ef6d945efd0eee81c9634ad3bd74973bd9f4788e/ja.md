```julia
add_component!(
    sys::PowerSystems.System,
    component::PowerSystems.Component;
    skip_validation,
    kwargs...
)

```

システムにコンポーネントを追加します。

コンポーネントは1つの`System`にしか追加できません。コンポーネントの名前がその具体的な型に対してすでに保存されている場合、ArgumentErrorがスローされます。コンポーネント固有のルールが違反されている場合、ArgumentErrorがスローされます。コンポーネントのフィールド値が定義された有効範囲の外にある場合、InvalidValueがスローされます。

# 例

```julia
sys = System(100.0)

# 単一のコンポーネントを追加します。
add_component!(sys, bus)

# 一度に多くを追加します。
buses = [bus1, bus2, bus3]
generators = [gen1, gen2, gen3]
foreach(x -> add_component!(sys, x), Iterators.flatten((buses, generators)))
```

[`add_components!`](@ref)も参照してください。
