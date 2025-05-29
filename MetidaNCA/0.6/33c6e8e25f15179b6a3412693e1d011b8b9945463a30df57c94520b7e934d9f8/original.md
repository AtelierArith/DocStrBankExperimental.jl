```
auc_sparse(time, obs)
```

AUC for sparse data.

$$
w_1 = (t_2 - t_1) / 2
$$

$$
w_j = (t_{j+1} - t_{j-1}) / 2  (2 \leq j \leq J - 1)
$$

$$
w_J = (t_J - t_{J-1}) / 2
$$

$$
AUC = \sum_{j=1}^J \mu_j w_j
$$

where `math \mu_j` is the mean drug concentration at time t.
