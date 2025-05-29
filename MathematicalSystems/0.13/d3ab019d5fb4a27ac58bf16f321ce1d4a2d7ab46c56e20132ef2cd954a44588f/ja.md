```
successor(system::ConstrainedDiscreteIdentitySystem, x::AbstractVector;
          [check_constraints]=true)
```

`ConstrainedDiscreteIdentitySystem`の後継状態を返します。

### 入力

  * `system`            – `ConstrainedDiscreteIdentitySystem`
  * `x`                 – 状態（任意のベクトル型である必要があります）
  * `check_constraints` – （オプション、デフォルト: `true`）状態が状態集合に属するかどうかを確認します

### 出力

同じ状態 `x`。
