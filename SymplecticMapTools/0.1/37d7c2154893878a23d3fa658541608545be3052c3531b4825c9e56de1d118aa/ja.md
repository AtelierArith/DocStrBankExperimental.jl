```
get_circle_info(hs::AbstractArray, c::AbstractArray; rattol::Number=1e-8,
                ratcutoff::Number=1e-4, max_island_d::Integer=30)
```

観測値 `hs` と学習したフィルター `c` から不変円のフーリエ表現を取得します（フィルターを見つけるには `adaptive_invariant_circle_model` と `invariant_circle_model` を参照してください）。円の事後検証については `get_circle_residual` を参照してください。

オプション引数:

  * `rattol`: 根は |ω-m/n|<rattol の場合に有理数と見なされます
  * `ratcutoff`: シーケンスが島であるかどうかを判断するために「重要」と見なされるために必要な線形モードの相対的な重要性
  * `max_island_d`: 島に対して考慮される最大分母。
  * `modetol`: フーリエモードの数を決定するために使用される許容誤差（通常は1未満）。数値が高いほど、最小二乗系の堅牢性を犠牲にしてより多くのフーリエモードが得られます。ノイズの多いデータの場合は、これを減少させて（例：0.5に）ください。

出力:

  * `z`: タイプ `FourierCircle` の不変円

```
