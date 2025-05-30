```
discretediag(samples::AbstractArray{<:Real,3}; frac=0.3, method=:weiss, nsim=1_000)
```

`samples`の形状は`(draws, chains, parameters)`の離散診断を計算します。

`method`は`:weiss`、`:hangartner`、`:DARBOOT`、`:MCBOOT`、`:billinsgley`、および`:billingsleyBOOT`のいずれかである必要があります。

# 参考文献

Benjamin E. Deonovic, & Brian J. Smith. (2017). Convergence diagnostics for MCMC draws of a categorical variable.
