```
GreedyVarSelection(m::Int)
```

グリーディ分散最小化アプローチによる誘導点選択。元々[1]で提案され、最近[2]で再検討された。`m`は望ましい誘導点の数です。

[1] - L. Foster, A. Waagen, N. Aijaz, M. Hurley, A. Luis, J. Rinsky, C. Satyavolu, M. J. Way, P. Gazis, and A. Srivastava. Stable and Efficient Gaussian Process Calculations. Journal of Machine Learning Research, 2009. [2] - D. R. Burt, C. E. Rasmussen, and M. van der Wilk. Convergence of Sparse Variational Inference in Gaussian Processes Regression. Journal of Machine Learning Research, 2020.
