```
UserKNN(
    data::DataAccessor,
    n_neighbors::Integer,
    normalize::Bool=false
)
```

[User-based CF using the Pearson correlation](https://dl.acm.org/citation.cfm?id=312682). `n_neighbors` represents number of neighbors $k$, and `normalize` specifies if weighted sum of neighbors' rating is normalized.

The technique gives a weight to a user-user pair by the following equation:

$$
s_{u, v} = \frac{ \sum_{i \in \mathcal{I}^+_{u \cap v}}  (r_{u, i} - \overline{r}_u) (r_{v, i} - \overline{r}_v)}
{ \sqrt{\sum_{i \in \mathcal{I}^+_{u \cap v}} (r_{u,i} - \overline{r}_u)^2} \sqrt{\sum_{i \in \mathcal{I}^+_{u \cap v}} (r_{v, i} - \overline{r}_v)^2} },
$$

where $\mathcal{I}^+_{u \cap v}$ is a set of items which were observed by both user $u$ and $v$, and $r_{u, i}$ indicates a $(u, i)$ element in $R$. Plus, $\overline{r}_u$ and $\overline{r}_v$ are respectively mean values of $r_{u, i}$ and $r_{v, i}$ over $i \in \mathcal{I}^+_{u \cap v}$. By using the weights, user-based CF selects the top-$k$ highest-weighted users (i.e., nearest neighbors) of a target user $u$, and predicts missing $r_{u, i}$ for $i \in \mathcal{I}^-_u$ as:

$$
r_{u, i} = \overline{r}_u + \frac{\sum^k_{t=1} \left(r_{\sigma(t), i} - \overline{r}_{\sigma(t)}\right) \cdot s_{u,\sigma(t)} }{ \sum^k_{t=1} s_{u,\sigma(t)} },
$$

where $\sigma(t)$ denotes the $t$-th nearest-neighborhood user. Ultimately, sorting items $\mathcal{I}^-_u$ by the predicted values enables us to make recommendation to a user $u$.

It should be noted that user-based CF is highly inefficient because gradually increasing massive users and their dynamic tastes require us to frequently recompute the similarities for every pairs of users.
