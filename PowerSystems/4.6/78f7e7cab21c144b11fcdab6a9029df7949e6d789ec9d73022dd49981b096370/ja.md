```julia
add_components!(sys::PowerSystems.System, components)

```

システムに多くのコンポーネントを一度に追加します。

コンポーネントは1つの`System`にしか追加できません。コンポーネントの名前がその具体的な型に対してすでに保存されている場合、ArgumentErrorをスローします。コンポーネント固有のルールが違反されている場合、ArgumentErrorをスローします。コンポーネントのフィールド値が定義された有効範囲の外にある場合、InvalidValueをスローします。

# 例

```julia
sys = System(100.0)

buses = [bus1, bus2, bus3]
generators = [gen1, gen2, gen3]
add_components!(sys, Iterators.flatten((buses, generators))
```
