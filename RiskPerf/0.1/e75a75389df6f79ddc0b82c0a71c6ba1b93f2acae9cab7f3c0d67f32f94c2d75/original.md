```
value_at_risk(returns, confidence, method; multiplier=1.0)
```

Computes the Value-at-Risk (VaR) for a given significance level `α` based on the chosen estimation method. The VaR value represents the maximum expected loss at a certain significance level `α`. For a more tail-risk focused measure, see `expected_shortfall`.

# Arguments

  * `returns`:     Vector of asset returns.
  * `α`:           Significance level, e.g. use `0.05` for 95% confidence, or `0.01` for 99% confidence.
  * `method`:      Distribution estimation method: `:historical`, `:gaussian` or `:cornish_fisher`.
  * `multiplier`:  Optional scalar multiplier, i.e. use `12` to annualize monthly returns, and use `252` to annualize daily returns.

# Methods

  * `:historical`:        Historical based on empirical distribution of returns.
  * `:gaussian`:          Gaussian distribution based on parametric fit (mean, variance).
  * `:cornish_fisher`:    Cornish-Fisher based on Gaussian parametric distribution fit adjusted for third and fourth moments (skewness, kurtosis). Cornish-Fisher expansion aims to approximate the quantile of a true distribution by using higher moments (skewness and kurtosis) of that distribution to adjust for its non-normality. See https://thema.u-cergy.fr/IMG/pdf/2017-21.pdf for details.

# Sources

  * Favre, Laurent and Galeano, Jose-Antonio (2002). Mean-Modified Value-at-Risk Optimization with Hedge Funds. Journal of Alternative Investment.
  * Amédée-Manesme, Charles-Olivier and Barthélémy, Fabrice and Maillard, Didier (2017). Computation of the Corrected Cornish–Fisher Expansion using the Response Surface Methodology: Application to VaR and CVaR. THEMA Working Paper n°2017-21, Université de Cergy-Pontoise, France.
