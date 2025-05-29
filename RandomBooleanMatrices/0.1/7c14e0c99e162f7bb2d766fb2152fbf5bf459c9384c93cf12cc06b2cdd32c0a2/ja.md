```
matrixrandomizer(m [,rng]; method = curveball)
```

行と列の合計を維持しながら、呼び出すたびにランダムなブール行列を返す行列生成関数を作成します。非ブール入力行列はブールとして解釈され、値が != 0 の場合は `true` となります。

# 例

``` m = rand(0:4, 5, 6) rmg = matrixrandomizer(m)

random1 = rand(rmg) random2 = rand(rmg) ```
