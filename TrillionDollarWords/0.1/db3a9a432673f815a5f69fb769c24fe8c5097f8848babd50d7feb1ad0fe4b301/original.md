```
load_market_data()
```

Load the combined market data from the artifact. This dataset combines the CPI, PPI and UST data used in the paper.

  * The `date` column is the date of the event.
  * The `value` columns is the value of the market indicator (CPI, PPI, or UST).
  * The `indicator` column is the market indicator (CPI, PPI, or UST).
  * The `maturity` column is the maturity of the UST (if applicable).
