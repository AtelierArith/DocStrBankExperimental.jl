```
put_assets_into_blocks_by_trading_frequency(
   ts::SortedDataFrame,
   obs_multiple_for_new_block::Real,
   func::Symbol,
   optional_parameters::NamedTuple = NamedTuple(),
)
```

This makes a DataFrame that describes how to estimate the covariance matrix blockwise.

### Inputs

  * `ts` - The tick data.
  * `obs_multiple_for_new_block` - The relative number of ticks needed before a new block is made. So if this is 1.2 that means a new group is made when one asset has 20% or more ticks than the slowest traded asset in the previous block.
  * `func` - A symbol representing the covariance estimation function to be used.
  * `optional_parameters` - Optional parameters to be used in the `func` function.

### Returns

  * A `DataFrame` representing what estimations should be performed. The order of rows in the `DataFrame` shows the order of estimation.

### References

Hautsch, N., Kyj, L.M. and Oomen, R.C.A. (2012), A blocking and regularization approach to high‐dimensional realized covariance estimation. J. Appl. Econ., 27: 625-645
