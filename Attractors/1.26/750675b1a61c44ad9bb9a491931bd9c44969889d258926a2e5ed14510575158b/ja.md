```
tipping_probabilities(basins_before, basins_after) → P
```

システムパラメータ（または時間強制）の変化前後の計算された盆地のチッピング確率を、[Kaszas2019](@cite)の定義に従って返します。

入力の`basins`は整数値の配列であり、整数はアトラクタを列挙します。例えば、[`basins_of_attraction`](@ref)の出力です。

## 説明

$$
\mathcal{B}_i(p)
$$

をパラメータ$p$におけるアトラクタ$A_i$の引力盆地とします。Kaszásらは、システムのパラメータが$p_- \to p_+$に変化したときの$A_i$から$A_j$へのチッピング確率を次のように定義します。

$$
P(A_i \to A_j | p_- \to p_+) =
\frac{|\mathcal{B}_j(p_+) \cap \mathcal{B}_i(p_-)|}{|\mathcal{B}_i(p_-)|}
$$

ここで、$|\cdot|$は単に囲まれた集合の体積です。$P(A_i \to A_j | p_- \to p_+)$の値は`P[i, j]`です。この方程式は非常に単純なことを説明しています：$p_-$における$A_i$の引力盆地と$p_+$におけるアトラクタ$A_j$の引力盆地の重なりはどのくらいかということです。`basins_before, basins_after`に`-1`の値が含まれている場合、それは発散する軌道に対応し、これは`P`のシステムの最後のアトラクタと見なされます。
