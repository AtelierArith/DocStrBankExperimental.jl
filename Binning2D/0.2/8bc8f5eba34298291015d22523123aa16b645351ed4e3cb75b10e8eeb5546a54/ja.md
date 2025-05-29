```julia
get_x_y_w(bb; threshold, scale)

```

`(x, y, w)` の三つ組を返すイテレータを返し、`w ≥ threshold` のものだけを保持します。

`threshold == 0` の場合、`w` の合計は 1 になりますが、これは維持されません。目的は、プロットのために外れ値を除去することであり、`threshold = 1e-3` またはそれに類似した値を使用します。
