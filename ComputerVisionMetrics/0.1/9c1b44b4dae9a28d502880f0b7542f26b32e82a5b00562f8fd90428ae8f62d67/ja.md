## `dice_metric`

```julia
dice_metric(prediction::AbstractArray, ground_truth::AbstractArray)
```

2つのバイナリマスク、`prediction`と`ground_truth`の間のDice係数（ソーレンセン–ダイス指数とも呼ばれる）を計算します。

Dice係数は、2つの集合の類似性を測定し、0（重複なし）から1（完全な重複）までの範囲です。

#### 引数

  * `predicted_segment`: 予測されたバイナリマスク。
  * `ground_truth_segment`: グラウンドトゥルースのバイナリマスク。

#### 戻り値

  * 2つのマスク間のDice係数の値。
