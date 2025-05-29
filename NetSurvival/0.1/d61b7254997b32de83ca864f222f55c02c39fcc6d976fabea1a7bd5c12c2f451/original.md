```
GraffeoTest
```

The Grafféo test is a log-rank type test and is typically used in net survival analysis to determine the impact of certain covariates in the study.

The null $(H_0)$ hypothesis tests the following assumption:

$$
\forall t \in [0,T], \Lambda_{E,g_1}(t) = \Lambda_{E,g_2}(t) = ... = \Lambda_{E,g_k}(t)
$$

where $G = {g_1,...,g_k}$ is a partition of $1,...,n$ consisting of disjoint groups of individuals that we wish to compare to each other.  For all group $g \in G$, let's denote the numerator and denominator of the Pohar Perme (partial) excess hazard estimators, restricted to individuals in the group, by: 

  * $\partial N_{E,g}(s) = \sum_{i \in g} \frac{\partial N_i(s)}{S_{P_i}(s)} - \frac{Y_i(s)}{S_{P_i}(s)}\partial\Lambda_{P_i}(s)$
  * $Y_{E,g}(s) = \sum_{i \in g} \frac{Y_i(s)}{S_{P_i}(s)}$
  * $R_{g}(s) = \frac{Y_{E,g}(s)}{\sum_{g\in G} Y_{E,g}(s)}$

Then, define the vector $\mathbf Z = \left(Z_{g_r}: r \in 1,...,k-1 \right)$ with entries: 

$$
Z_g(T) = N_{E,g}(s) - \int_{0}^T Y_{E,g}(s) \partial\hat{\Lambda}_E(s)
$$

The test statistic is then given by:

$$
U(T) = \mathbf Z(T)'\hat{\Sigma}_Z^{-1} \mathbf Z(T)
$$

where the entries of the $\hat{\Sigma}_Z$ matrix are given by: 

$$
\sigma_{g,h}(T) = \int_0^T \sum_{\ell \in G} \left(\delta_{g,\ell} - R_g(t) \right)\left(\delta_{h,\ell} - R_h(t)\right) \left(\sum_{i\in\ell} \frac{\partial N_i(s)}{S^2_{P_i}}\right)
$$

Under $H_0$, the statistic $U(T)$ is asymptotically $\chi^2(k-1)$-distributed.

To apply the test to your data based on a certain rate table, apply the example below to your code : 

```
fit(GraffeoTest, @formula(Surv(time,status)~covariable1 + covariable2), data, ratetable)
```

If you wish to stratify a covariate:

```
fit(GraffeoTest, @formula(Surv(time,status)~covariable1 + Strata(covariable2)), data, ratetable)
```

The produced test statistics is supposed to follow a chi squared distribution under $(H_0)$. You can fetch the results using the `.stat`, `.df` and `.pval` fields of the returned object. 

References: 

  * [Graffeo2016](@cite) Grafféo, Nathalie and Castell, Fabienne and Belot, Aurélien and Giorgi, Roch (2016). A Log-Rank-Type Test to Compare Net Survival Distributions.
