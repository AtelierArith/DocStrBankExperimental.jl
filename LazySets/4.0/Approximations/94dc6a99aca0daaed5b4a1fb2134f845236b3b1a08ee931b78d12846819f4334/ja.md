```
box_approximation(ch::ConvexHull; [algorithm]::String="box")
```

凸包をタイトなハイパーレクタングルで過大評価します。

### 入力

  * `ch`        – 凸包
  * `algorithm` – （オプション; デフォルト: `"box"`）アルゴリズムの選択

### 出力

ハイパーレクタングル。

### アルゴリズム

`X` と `Y` を `ch` の2つの集合とします。次の性質を利用します：

$$
□(CH(X, Y))
    = □\left( X ∪ Y \right)
    = □\left( □(X) ∪ □(Y) \right)
$$

`algorithm == "extrema"` の場合、`extrema` を使用して `X` と `Y` の低い座標と高い座標を計算します。

`algorithm == "box"` の場合、代わりに `box_approximation` を使用して `X` と `Y` のボックス近似を計算します。

どちらの場合も、結果のボックス近似を取ります。

`"extrema"` アルゴリズムは、`extrema` が効率的であれば、間接的なハイパーレクタングルを割り当てる必要がないため、より効率的です。
