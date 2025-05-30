```
greensfunctions(i::Integer,j::Integer,σ::Array{ComplexF64,1},A)
```

グリーン関数の行列要素を計算します：

$$
G_{ij}(\sigma_k) = \left[ (\sigma_k I - A)^{-1} \right]_{ij},
$$

縮小シフト共役勾配法を用いて（参照：Y. Nagai, Y. Shinohara, Y. Futamura, および T. Sakurai,[arXiv:1607.03992v2 または DOI:10.7566/JPSJ.86.014708]）。異なる周波数 $\sigma_k$ で同時に $G_{ij}(\sigma_k)$ を取得できます。

入力：

  * `i` : グリーン関数のインデックス
  * `j` : グリーン関数のインデックス
  * `σ` : 周波数
  * `A` : エルミート行列。配列、線形マップ、スパース配列を使用できます。
  * `eps` : 残差（オプション）デフォルト：`1e-12`
  * `maximumsteps` : 最大ステップ数（オプション）デフォルト：`20000`

出力：

  * `Gij[1:M]` : $\sigma_k$ によって定義された M 周波数でのグリーン関数の行列要素。
