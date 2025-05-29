```
trsyl3!(transa, transb, A, B, C, isgn=1) -> (C, scale)
```

シルベスター行列方程式 `A * X +/- X * B = scale*C` を解きます。ここで `A` と `B` はどちらも準上三角です。`transa = N` の場合、`A` は変更されません。`transa = T` の場合、`A` は転置されます。`transa = C` の場合、`A` は共役転置されます。同様に `transb` と `B` に対しても適用されます。`isgn = 1` の場合、方程式 `A * X + X * B = scale * C` が解かれます。`isgn = -1` の場合、方程式 `A * X - X * B = scale * C` が解かれます。

`X`（`C` を上書き）と `scale` を返します。

[1] と [2] のブロックアルゴリズムが使用されます。

参考文献: [1] E. S. Quintana-Orti と R. A. Van De Geijn (2003). アルゴリズムの形式的導出: 三角シルベスター方程式, ACM Transactions on Mathematical Software (TOMS), ボリューム 29, ページ 218-243.

[2] A. Schwarz と C. C. Kjelgaard Mikkelsen (2020). 三角シルベスター方程式の堅牢なタスク並列解法. Lecture Notes in Computer Science, vol 12043, ページ 82-92, Springer.
