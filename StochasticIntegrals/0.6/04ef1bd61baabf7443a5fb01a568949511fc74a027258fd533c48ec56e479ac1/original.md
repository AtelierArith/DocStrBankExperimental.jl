```
correlation(ito::ItoSet, index1::Integer, index2::Integer)
correlation(ito::ItoSet, brownian_id1::Symbol, brownian_id2::Symbol)
```

Get correlation between brownian motions in an `ItoSet`.

### Inputs

  * `ito` - An `ItoSet` that you want the correlation for two itos within.
  * `index1` or `brownian_id1` - The index/key for the first ito integral.
  * `index2` or `brownian_id2` - The index/key for the second ito integral.

### Returns

  * A scalar
