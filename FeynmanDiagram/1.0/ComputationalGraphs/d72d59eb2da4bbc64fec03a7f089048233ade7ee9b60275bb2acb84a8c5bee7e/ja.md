```
function merge_linear_combination(g::AbstractGraph)

計算グラフ `g` のコピーを返し、乗法的な前因子を因数分解します。
例えば、3*g1 + 5*g2 + 7*g1 + 9*g2 ↦ 10*g1 + 14*g2 = linear_combination(g1, g2, 10, 14)。
ユニークなサブグラフとその合計前因子の線形結合を返します。
グラフ `g` が Sum 操作を表さない場合は何もしません。
```

# 引数:

  * `g::AbstractGraph`: 修正されるグラフ
