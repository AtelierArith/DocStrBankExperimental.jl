```
successor(system::AbstractDiscreteSystem,
          x::AbstractVector, u::AbstractVector, w::AbstractVector; [check_constraints]=true)
```

`AbstractDiscreteSystem`の後継状態を返します。

### 入力

  * `system`            – `AbstractDiscreteSystem`
  * `x`                 – 状態（任意のベクトル型である必要があります）
  * `u`                 – 入力（任意のベクトル型である必要があります）
  * `w`                 – ノイズ（任意のベクトル型である必要があります）
  * `check_constraints` – （オプション、デフォルト: `true`）状態が状態集合に属するかどうかを確認します

### 出力

状態 `x`、入力 `u`、およびノイズ `w` にシステムを適用した結果。
