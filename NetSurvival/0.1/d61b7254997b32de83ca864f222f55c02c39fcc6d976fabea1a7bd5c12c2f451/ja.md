```
GraffeoTest
```

Grafféoテストはログランク型のテストであり、通常はネット生存分析において、研究における特定の共変量の影響を判断するために使用されます。

帰無仮説 $(H_0)$ は以下の仮定をテストします：

$$
\forall t \in [0,T], \Lambda_{E,g_1}(t) = \Lambda_{E,g_2}(t) = ... = \Lambda_{E,g_k}(t)
$$

ここで、$G = {g_1,...,g_k}$ は、互いに比較したい個人の不連続グループからなる $1,...,n$ の分割です。すべてのグループ $g \in G$ に対して、グループ内の個人に制限されたPohar Perme（部分的）超過ハザード推定量の分子と分母を次のように示します：

  * $$
    \partial N_{E,g}(s) = \sum_{i \in g} \frac{\partial N_i(s)}{S_{P_i}(s)} - \frac{Y_i(s)}{S_{P_i}(s)}\partial\Lambda_{P_i}(s)
    $$
  * $$
    Y_{E,g}(s) = \sum_{i \in g} \frac{Y_i(s)}{S_{P_i}(s)}
    $$
  * $$
    R_{g}(s) = \frac{Y_{E,g}(s)}{\sum_{g\in G} Y_{E,g}(s)}
    $$

次に、ベクトル $\mathbf Z = \left(Z_{g_r}: r \in 1,...,k-1 \right)$ を次のように定義します：

$$
Z_g(T) = N_{E,g}(s) - \int_{0}^T Y_{E,g}(s) \partial\hat{\Lambda}_E(s)
$$

テスト統計量は次のように与えられます：

$$
U(T) = \mathbf Z(T)'\hat{\Sigma}_Z^{-1} \mathbf Z(T)
$$

ここで、$\hat{\Sigma}_Z$ 行列のエントリは次のように与えられます：

$$
\sigma_{g,h}(T) = \int_0^T \sum_{\ell \in G} \left(\delta_{g,\ell} - R_g(t) \right)\left(\delta_{h,\ell} - R_h(t)\right) \left(\sum_{i\in\ell} \frac{\partial N_i(s)}{S^2_{P_i}}\right)
$$

$$
H_0
$$

の下で、統計量 $U(T)$ は漸近的に $\chi^2(k-1)$ 分布に従います。

特定のレートテーブルに基づいてデータにテストを適用するには、以下の例をコードに適用してください：

```
fit(GraffeoTest, @formula(Surv(time,status)~covariable1 + covariable2), data, ratetable)
```

共変量を層別化したい場合：

```
fit(GraffeoTest, @formula(Surv(time,status)~covariable1 + Strata(covariable2)), data, ratetable)
```

生成されたテスト統計量は、$(H_0)$ の下でカイ二乗分布に従うと考えられています。返されたオブジェクトの `.stat`、`.df`、および `.pval` フィールドを使用して結果を取得できます。

参考文献：

  * [Graffeo2016](@cite) Grafféo, Nathalie and Castell, Fabienne and Belot, Aurélien and Giorgi, Roch (2016). A Log-Rank-Type Test to Compare Net Survival Distributions.
