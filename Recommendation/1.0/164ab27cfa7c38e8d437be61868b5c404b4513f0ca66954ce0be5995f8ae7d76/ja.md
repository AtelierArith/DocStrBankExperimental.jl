```
SVD(
    data::DataAccessor,
    n_factors::Integer
)
```

ユーザー-アイテム行列 $R \in \mathbb{R}^{|\mathcal{U}| \times |\mathcal{I}|}$ の SVD に基づく推薦は、元々 [Sarwar et al.](http://files.grouplens.org/papers/webKDD00.pdf) によって研究されました。ランク $k$ は `n_factors` によって設定されます。スパース行列は `data.R` ではサポートされていません。

推薦の文脈において、$U_k \in \mathbb{R}^{|\mathcal{U}| \times k}$、$V \in \mathbb{R}^{|\mathcal{I}| \times k}$ および $\Sigma \in \mathbb{R}^{k \times k}$ はそれぞれ $k$ ユーザー/アイテム特徴ベクトルと対応する重みとして見なされます。低ランク近似のアイデアは、直感的には元の行列の *圧縮* または *ノイズ除去* として機能し、ランク-$k$ 行列 $A_k$ の各要素は $A$ の元の要素の最良の *圧縮*（または *ノイズ除去*）値を保持します。したがって、$R_k = \mathrm{SVD}_k(R)$ は $R$ の最良のランク-$k$ 近似であり、基礎となるユーザーの好みをできるだけ多く捉えます。一度 $R$ が $U, \Sigma$ および $V$ に分解されると、$\sum^k_{j=1} \sigma_j u_{u, j} v_{i, j}$ によって計算された $R_k$ の $(u, i)$ 要素は、ユーザー-アイテムペアの予測となる可能性があります。
