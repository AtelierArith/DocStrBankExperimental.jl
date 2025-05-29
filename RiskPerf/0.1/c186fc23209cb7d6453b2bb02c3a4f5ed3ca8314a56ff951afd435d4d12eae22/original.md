```
adjusted_sharpe_ratio(returns; multiplier=1.0, risk_free=0.0)
```

Calculates the adjusted Sharpe Ratio introduced by Pezier and White (2006) by penalizing negative skewness and excess kurtosis.

# Formula

$\text{SR} = \dfrac{\mathbb{E}\left[ \text{returns} - \text{risk\_free}\right ]}{\sigma(\text{returns} - \text{risk\_free})}$

$\text{ASR} = \text{SR} \left[1 + \frac{S}{6}\text{SR} - \frac{K-3}{24}\text{SR}^2\right] \times \sqrt{\text{multiplier}}$

# Arguments

  * `returns`:        Vector of asset returns.
  * `multiplier`:     Optional scalar multiplier, i.e. use `12` to annualize monthly returns, and use `252` to annualize daily returns.
  * `risk_free`:      Optional vector or scalar value denoting the risk-free return (must have same frequency as the provided returns, e.g. daily).

# Sources

  * Pezier, Jaques and White, Anthony (2006). The Relative Merits of Investable Hedge Fund Indices and of Funds of Hedge Funds in Optimal Passive Portfolios. ICMA Centre Discussion Papers in Finance.
