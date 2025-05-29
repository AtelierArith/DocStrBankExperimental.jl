```
ItemKNN(
    data::DataAccessor,
    n_neighbors::Integer
)
```

[Item-based CF](https://dl.acm.org/citation.cfm?id=963776) that provides a way to model item-item concepts by utilizing the similarities of items in the CF paradigm. `n_neighbors` represents number of neighbors $k$.

Item properties are relatively stable compared to the users' tastes, and the number of items is generally smaller than the number of users. Hence, while user-based CF successfully captures the similarities of users' complex tastes, modeling item-item concepts could be much more promising in terms of both scalability and overall accuracy.

Item-based CF defines a similarity between an item $i$ and $j$ as:

$$
s_{i,j} = \frac{ \sum_{u \in \mathcal{U}_{i \cap j}}  (r_{u, i} - \overline{r}_i) (r_{u, j} - \overline{r}_j)}
{ \sqrt{\sum_{u \in \mathcal{U}_{i \cap j}} (r_{u,i} - \overline{r}_i)^2} \sqrt{\sum_{u \in \mathcal{U}_{i \cap j}} (r_{u, j} - \overline{r}_j)^2} },
$$

where $\mathcal{U}_{i \cap j}$ is a set of users that both of $r_{u,i}$ and $r_{u, j}$ are not missing, and $\overline{r}_i, \overline{r}_j$ are mean values of $i$-th and $j$-th column in $R$. Similarly to the user-based algorithm, for the $t$-th nearest-neighborhood item $\tau(t)$, prediction can be done by top-$k$ weighted sum of target user's feedbacks:

$$
r_{u,i} = \frac{\sum^k_{t=1} s_{i,\tau(t)} \cdot r_{u,\tau(t)} }{ \sum^k_{t=1} s_{i,\tau(t)} }.
$$

In case that the number of items is smaller than users, item-based CF could be a more reasonable choice than the user-based approach.
