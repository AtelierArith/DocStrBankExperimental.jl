```
func get_parameters(ode; initial_conditions=true)
```

`ode` システムからパラメータを取得します。`initial_conditions` が `true` に設定されている場合は初期条件を取得します。

## 入力

```
- `ode::ODE` - ODE システム
- `initial_conditions::Bool` - 初期条件を抽出するかどうか。デフォルトは `true`。
```

## 出力

```
    - パラメータ（および初期条件）の配列。
```
