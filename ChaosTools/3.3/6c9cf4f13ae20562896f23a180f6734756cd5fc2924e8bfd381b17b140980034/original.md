```
dyca(data, eig_threshold) -> eigenvalues, proj_mat, projected_data
```

Compute the Dynamical Component analysis (DyCA) of the given `data` [^Uhl2018] used for dimensionality reduction.

Return the eigenvalues, projection matrix, and reduced-dimension data (which are just `data*proj_mat`).

## Keyword Arguments

  * norm_eigenvectors=false : if true, normalize the eigenvectors

## Description

Dynamical Component Analysis (DyCA) is a method to detect projection vectors to reduce the dimensionality of multi-variate, high-dimensional deterministic datasets. Unlike methods like PCA or ICA that make a stochasticity assumption, DyCA relies on a determinacy assumption on the time-series and is based on the solution of a generalized eigenvalue problem. After choosing an appropriate eigenvalue threshold and solving the eigenvalue problem, the obtained eigenvectors are used to project the high-dimensional dataset onto a lower dimension. The obtained eigenvalues measure the quality of the assumption of linear determinism for the investigated data. Furthermore, the number of the generalized eigenvalues with a value of approximately 1.0 are a measure of the number of linear equations contained in the dataset. This property is useful in detecting regions with highly deterministic parts in the time-series and also as a preprocessing step for reservoir computing of high-dimensional spatio-temporal data.

The generalised eigenvalue problem we solve is:

$$
C_1 C_0^{-1} C_1^{\top} \bar{u} = \lambda C_2 \bar{u}

$$

where $C_0$ is the correlation matrix of the data with itself, $C_1$ the correlation matrix of the data with its derivative, and $C_2$ the correlation matrix of the derivative of the data with itself. The eigenvectors $\bar{u}$ with eigenvalues approximately 1 and their $C_1^{-1} C_2 u$ counterpart, form the space where the data is projected onto.

[^Uhl2018]: B Seifert, K Korn, S Hartmann, C Uhl, *Dynamical Component Analysis (DYCA): Dimensionality Reduction for High-Dimensional Deterministic Time-Series*, 10.1109/mlsp.2018.8517024, 2018 IEEE 28th International Workshop on Machine Learning for Signal Processing (MLSP)
