```
set_control_value(id::Integer, control_type::ASI_CONTROL_TYPE, value, auto::Bool=false)
```

指定された値に制御（例：露出）を設定します。指定された値が範囲外の場合は、自動的に最小または最大を設定します。

# 引数:

```
id: カメラID
control_type: 設定する制御タイプ（例：露出またはゲイン）。
value: 制御が設定される値。
auto: 制御が自動的に設定されるべきかどうか。
    事前にこの制御がサポートされているか確認してください。
```

# 例外:

```
ASIError
```
