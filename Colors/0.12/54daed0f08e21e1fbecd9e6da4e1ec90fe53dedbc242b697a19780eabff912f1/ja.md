```
colors = distinguishable_colors(n, seed=RGB{N0f8}[];
                                dropseed=false,
                                transform=identity,
                                lchoices=range(0, stop=100, length=15),
                                cchoices=range(0, stop=100, length=15),
                                hchoices=range(0, stop=342, length=20))
```

n 個の最大限に区別可能な色を生成します。

これは、n 色を最大限に区別可能なものとして選択するための貪欲なブルートフォースアプローチを使用します。シード色と、可能な色相、彩度、明度の値のセット（LCHab 空間内）を考慮し、パレット内の既存の色との最小ペアワイズ距離を最大化する色を繰り返し選択します。

# 引数

  * `n`: 生成する色の数。
  * `seed`: パレットに含まれる初期色。

# キーワード引数

  * `dropseed`: true の場合、`seed` 値は削除されます。これは、選択された色がシード値から区別可能であることを保証するための簡単なメカニズムを提供します。true の場合、`n` はシード色を含みません。
  * `transform`: 距離を測定する前に色に適用される変換。デフォルトは `identity` で、他の選択肢には色盲をシミュレートするための `deuteranopic` があります。
  * `lchoices`: 可能な明度の値
  * `cchoices`: 可能な彩度の値
  * `hchoices`: 可能な色相の値

指定された `seed` の型の長さ `n` の色の `Vector` を返します。
