```
usd_cr(y1, y2; source=gdp, future=nothing) -> r
```

Computes a conversion rate from USD in `y1` to USD in `y2`.

Optional keyword arguments:

  * `source` - choose between `gdp` and `cpi`, defaults to `gdp`
  * `future` - assumed future inflation rate.  can be either:

      * `nothing` (default) - throw an error when a year outside of the range is given
      * `rate` - the assumed rate of inflation for years beyond the max year i.e. `0.02` for 2% inflation rate

Input Data Sources:

  * `gdp` - Updated with 2021 data from [bea.gov](https://apps.bea.gov/iTable/iTable.cfm?reqid=19&step=3&isuri=1&1921=survey), Table 1.1.9.
  * `cpi` - Updated with 2021 data from [bls.gov](https://data.bls.gov/timeseries/CUUR0000SA0)
