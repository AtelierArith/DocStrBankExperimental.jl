```
compose(b1, b2, bs...; normalize_stepsize=false)
```

B系列 `b1`、`b2`、`bs...` を合成します。すべてのB系列が空の木の係数が1であると仮定します。

Chartier、Hairer、Vilmart（2010）の表記法では、`compose(b1, b2, b3) = b1 ⋅ b2 ⋅ b3` となります。この積は結合的であり、左から右に読む必要があります。つまり、メソッド `b1` が最初に適用され、その後に `b2`、`bs...` が続きます。

`normalize_stepsize = true` の場合、返されるB系列の係数は、各根付き木 `t` に対して `n^order(t)` で割られます。ここで、`n` は合成されたB系列の総数です。これにより、ステップサイズが正規化され、結果として得られる数値積分器B系列は、入力系列と同じステップサイズを使用します（`n` 倍のステップサイズではなく）。

# 参考文献

以下のセクション3.1

  * Philippe Chartier, Ernst Hairer, Gilles Vilmart (2010) Algebraic Structures of B-series. Foundations of Computational Mathematics [DOI: 10.1007/s10208-010-9065-1](https://doi.org/10.1007/s10208-010-9065-1)
