```
vector_field(system::ConstrainedContinuousIdentitySystem, x::AbstractVector;
          [check_constraints]=true)
```

`ConstrainedContinuousIdentitySystem`のベクトルフィールド状態を返します。

### 入力

  * `system`            – `ConstrainedContinuousIdentitySystem`
  * `x`                 – 状態（任意のベクトル型である必要があります）
  * `check_constraints` – （オプション、デフォルト: `true`）状態が状態集合に属するかどうかを確認します

### 出力

次元`statedim`のゼロベクトル。
