```
expected_shortfall(returns, confidence, method; multiplier=1.0)
```

Computes the Expected Shortfall (ES), also known as Conditional Value-at-Risk (CVaR), Average Value-at-Risk (AVaR) or Expected Tail Loss (ETL). The ES is the expected return on the asset in the worst `α%` of cases, therefore quantifies the tail-risk of an asset. It is calculated by averaging all of the returns in the distribution that are worse than the VaR of the portfolio at a given significance level `α`. For instance, for a 5% significance level, the expected shortfall is calculated by taking the average of returns in the worst 5% of cases.

Expected Shortfall puts emphasis on the tail of the loss distribution, whereas Value-at-risk neglects this aspect.

# Arguments

  * `returns`:        Vector of asset returns.
  * `α`:              Significance level, e.g. use `0.05` for 95% confidence, or `0.01` for 99% confidence.
  * `method`:         Distribution estimation method: `:historical`, `:gaussian` or `:cornish_fisher`.
  * `multiplier`:     Optional scalar multiplier, i.e. use `12` to annualize monthly returns, and use `252` to annualize daily returns.

# Methods

  * `:historical`:        Historical based on empirical distribution of returns.
  * `:gaussian`:          Gaussian distribution based on parametric fit (mean, variance).
  * `:cornish_fisher`:    Cornish-Fisher based on Gaussian parametric distribution fit adjusted for third and fourth moments (skewness, kurtosis). Cornish-Fisher expansion aims to approximate the quantile of a true distribution by using higher moments (skewness and kurtosis) of that distribution to adjust for its non-normality. See [https://thema.u-cergy.fr/IMG/pdf/2017-21.pdf](https://thema.u-cergy.fr/IMG/pdf/2017-21.pdf) for details.

# Sources

  * Amédée-Manesme, Charles-Olivier and Barthélémy, Fabrice and Maillard, Didier (2017). Computation of the Corrected Cornish–Fisher Expansion using the Response Surface Methodology: Application to VaR and CVaR. THEMA Working Paper n°2017-21, Université de Cergy-Pontoise, France.
