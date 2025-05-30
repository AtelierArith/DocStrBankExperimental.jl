```
successor(system::AbstractDiscreteSystem, x::AbstractVector, u::AbstractVector;
          [check_constraints]=true)
```

`AbstractDiscreteSystem`の後継状態を返します。

### 入力

  * `system`            – `AbstractDiscreteSystem`
  * `x`                 – 状態（任意のベクトル型である必要があります）
  * `u`                 – 入力（任意のベクトル型である必要があります）またはノイズ、`system`が制御されていない場合
  * `check_constraints` – （オプション、デフォルト: `true`）状態が状態集合に属するかどうかを確認します

### 出力

状態 `x` と入力 `u` にシステムを適用した結果。

### 注意事項

システムが制御されていないがノイズがある場合、入力 `u` はノイズとして解釈されます。
