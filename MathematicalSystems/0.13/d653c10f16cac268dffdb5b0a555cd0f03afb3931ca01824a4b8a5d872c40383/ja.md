```
ConstrainedBlackBoxControlMap
```

制約付きブラックボックス制御マップの形式

$$
    (x, u) ↦ h(x, u), x ∈ \mathcal{X}, u ∈ \mathcal{U}.
$$

### フィールド

  * `dim`  – 状態次元
  * `input_dim` – 入力次元
  * `output_dim` – 出力次元
  * `h` – 出力関数
  * `X` – 状態制約
  * `U` – 入力制約
