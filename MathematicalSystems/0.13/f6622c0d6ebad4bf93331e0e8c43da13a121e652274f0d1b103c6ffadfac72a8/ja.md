```
vector_field(system::AbstractContinuousSystem, x::AbstractVector;
          [check_constraints]=true)
```

`AbstractContinuousSystem`のベクトルフィールド状態を返します。

### 入力

  * `system`            – `AbstractContinuousSystem`
  * `x`                 – 状態（任意のベクトル型である必要があります）
  * `check_constraints` – （オプション、デフォルト: `true`）状態が状態集合に属するかどうかを確認します

### 出力

状態 `x` におけるシステムのベクトルフィールド。
