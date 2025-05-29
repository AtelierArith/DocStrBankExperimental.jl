```
SVDD_train(K, nu)
```

train a one class support vecort machine model (i.e. support vector data description), given a kernel matrix K and and the highest possible percentage of outliers `nu`. Returns the model object (`svdd_model`). Requires LIBSVM.

Tax, D. M. J., & Duin, R. P. W. (1999). Support vector domain description. Pattern Recognition Letters, 20, 1191–1199. Schölkopf, B., Williamson, R. C., & Bartlett, P. L. (2000). New Support Vector Algorithms. Neural Computation, 12, 1207–1245.
