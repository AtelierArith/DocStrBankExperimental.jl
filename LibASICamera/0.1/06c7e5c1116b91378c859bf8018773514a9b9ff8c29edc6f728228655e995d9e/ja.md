```
get_control_value(id::Integer, control_type::ASI_CONTROL_TYPE)
```

現在の制御値の設定を取得します。例えば、露出やゲインなどです。

# 引数:

```
id: カメラID
control_type: 取得する制御タイプ。例えば、露出やゲインなど。
```

# 戻り値:

```
タプル (value, is_auto)
```

# 例外:

```
ASIError
```
