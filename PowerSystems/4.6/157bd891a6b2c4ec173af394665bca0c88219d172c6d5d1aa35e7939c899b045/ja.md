```julia
convert_component!(
    sys::PowerSystems.System,
    old_load::PowerSystems.PowerLoad,
    new_type::Type{PowerSystems.StandardLoad};
    kwargs...
)

```

PowerLoadコンポーネントをStandardLoadコンポーネントに変換し、システム内の元のコンポーネントを置き換えます。PowerLoadに相当しないStandardLoadのフィールドは設定されません。
