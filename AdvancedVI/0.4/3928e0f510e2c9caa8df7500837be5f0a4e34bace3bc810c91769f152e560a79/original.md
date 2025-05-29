```
PolynomialAveraging(eta)
```

Polynomial averaging rule proposed Shamir and Zhang[^SZ2013]. At iteration `t`, the parameter average $ \bar{\lambda}_t $ according to the polynomial averaging rule is given as

$$
    \bar{\lambda}_t = (1 - w_t) \bar{\lambda}_{t-1} + w_t \lambda_t \, ,
$$

where the averaging weight is 

$$
    w_t = \frac{\eta + 1}{t + \eta} \, .
$$

Higher `eta` ($\eta$) down-weights earlier iterations. When $\eta=0$, this is equivalent to uniformly averaging the iterates in an online fashion. The DoG paper[^IHC2023] suggests $\eta=8$.

# Parameters

  * `eta`: Regularization term. (default: `8`)

[^SZ2013]: Shamir, O., & Zhang, T. (2013). Stochastic gradient descent for non-smooth optimization: Convergence results and optimal averaging schemes. In International conference on machine learning (pp. 71-79). PMLR.
