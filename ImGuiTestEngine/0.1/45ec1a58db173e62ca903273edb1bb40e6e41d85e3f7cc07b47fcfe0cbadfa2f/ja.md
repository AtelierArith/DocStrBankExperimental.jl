```julia
SetRef(test_ref::Union{Int64, String})
SetRef(test_ref::Union{Int64, String}, ctx)

```

現在の参照を設定します。参照の詳細については、[上流のドキュメント](https://github.com/ocornut/imgui_test_engine/wiki/Named-References)を参照してください。

# 例

```julia
@register_test(engine, "foo", "bar") do ctx
    SetRef("My Window")
end
```

`test_ref`は*常に*絶対参照として扱われることに注意してください：

```julia
@register_test(engine, "foo", "bar") do ctx
    SetRef("My Window/quux") # これは参照を`//My Window/quux`に設定します

    # これらの2つの呼び出しは機能しません
    SetRef("My Window") # 参照を`//My Window`に設定します
    SetRef("quux")      # 参照を`//quux`に設定しようとします
end
```
