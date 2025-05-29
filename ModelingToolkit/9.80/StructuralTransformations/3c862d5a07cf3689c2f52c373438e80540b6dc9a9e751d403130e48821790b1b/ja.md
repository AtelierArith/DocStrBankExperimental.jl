```julia
check_consistency(
    state::ModelingToolkit.TransformationState,
    orig_inputs;
    nothrow
) -> Bool

```

`state`の整合性を、入力`orig_inputs`を考慮してチェックします。`nothrow == false`の場合、システムが過不足決定または特異である場合にエラーをスローします。この場合、関数が返されると`true`が返されます。`nothrow == true`の場合、エラーをスローする代わりに`false`が返されます。特異な場合は警告が表示されます。
