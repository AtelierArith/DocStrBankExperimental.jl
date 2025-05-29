```julia
check_component(
    sys::PowerSystems.System,
    component::PowerSystems.Component
)

```

コンポーネントの値をチェックします。

コンポーネントのフィールド値が定義された有効範囲外である場合や、タイプのカスタム検証メソッドがチェックに失敗した場合は、InvalidValueをスローします。
