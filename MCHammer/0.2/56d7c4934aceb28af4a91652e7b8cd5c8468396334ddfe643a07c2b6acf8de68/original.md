```
GBMA_d(price_0, t, rf, exp_vol; rng="none")
```

GBMA_d allows you to forecast the stock price at a given day in the future. This function uses a multiplicative Geometric Brownian Motion to forecast but using the Black-Scholes approach

```
**price_0**: Stock Price at period 0
**t**: Number of days out to forecast
**rf**: Risk free rate (usually the country's 25 or 30 bond)
**exp_vol**: Expected volatility is the annual volatility
**rng**: Used seed the results to make the forecast reproducible. Set to none by default which means fully random  but can use any of Julia's rngs to seed results. e.g. *GBMA_d(price_0, t, rf, exp_vol; rng=MersenneTwister(1))*
```
