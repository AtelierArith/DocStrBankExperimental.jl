```
t = find_threshold(histogram, edges, Balanced())
t = find_threshold(img, Balanced(); nbins = 256)
```

バランスの取れたヒストグラムのしきい値処理では、ビンをその占有数に等しい質量を持つ物理的な重さとして解釈します。バランスの取れたヒストグラム手法は、次の3つのステップを繰り返します：(1) 中間ビンインデックスを「ピボット」として選択し、(2) ピボットビンの左側と右側の合計重量を計算し、(3) 左側が最も重い場合は最も左のビンを削除し、そうでない場合は最も右のビンを削除します。アルゴリズムは、単一のビンのみが残るまで停止します。最後のビンが求められるしきい値を決定します。

# 出力

実数 `t` を `edges` に返します。`edges` パラメータは、ヒストグラムビンに関連付けられた区間を指定する `AbstractRange` を表します。

# 拡張ヘルプ

# 詳細

$$
f_n
$$

($n = 1 \ldots N$) をヒストグラムの $n$ 番目のビンの観測数とします。バランスの取れたヒストグラム手法は、入れ子の区間のシーケンスを構築します。

$$
[1,N] \cap \mathbb{Z} \supset I_2 \supset I_3 \supset \ldots \supset I_{N-1},
$$

ここで、$k = 2 \ldots N-1$ の場合

$$
I_k = \begin{cases}
   I_{k-1} \setminus \{\min \left( I_{k-1} \right) \} &\text{if } \sum_{n = \min \left( I_{k-1} \right)}^{I_m}f_n \gt   \sum_{n =  I_m + 1}^{ \max \left( I_{k-1} \right)} f_n, \\
   I_{k-1} \setminus \{\max \left( I_{k-1} \right) \} &\text{otherwise},
\end{cases}
$$

そして $I_m = \lfloor \frac{1}{2}\left(  \min \left( I_{k-1} \right) +  \max \left( I_{k-1} \right) \right) \rfloor$。最終区間 $I_{N-1}$ は、求められるしきい値に対応するビンインデックスの単一の要素で構成されます。

ビンをその占有数に等しい質量を持つ物理的な重さとして解釈すると、アルゴリズムの各ステップは、ピボットの周りで結果のヒストグラムを「バランス」させるために最も左または最も右のビンを削除することとして概念化できます。ピボットは、考慮中の区間の開始点と終了点の間の中間点として定義されます。

もし $I_{N-1}$ の単一の要素が $1$ または $N$ に等しい場合、元のヒストグラムは単一のピークを持ち、アルゴリズムは適切なしきい値を見つけることに失敗したことになります。この場合、アルゴリズムは `UnimodalRosin` メソッドを使用してしきい値を選択することに戻ります。

# 引数

関数の引数は以下でより詳細に説明されています。

## `histogram`

頻度分布を格納する `AbstractArray`。

## `edges`

頻度分布の区間がどのように分割されるかを指定する `AbstractRange`。

# 例

`TestImages` パッケージの「カメラマン」画像のしきい値を計算します。

```julia

using TestImages, ImageContrastAdjustment, HistogramThresholding

img = testimage("cameraman")
edges, counts = build_histogram(img, 256)
#=
  `counts` 配列は、最初のビンエッジよりも低い頻度をインデックス 0 に格納します。
  `edges` によって区切られた区間でしきい値を求めているため、
  `counts` の最初のビンを破棄する必要があります。
  そうすることで、`edges` と `counts` の次元が一致します。
=#
t = find_threshold(counts[1:end], edges, Balanced())
```

# 参考文献

1. “BI-LEVEL IMAGE THRESHOLDING - A Fast Method”, Proceedings of the First International Conference on Bio-inspired Systems and Signal Processing, 2008. Available: [10.5220/0001064300700076](https://doi.org/10.5220/0001064300700076)

```
