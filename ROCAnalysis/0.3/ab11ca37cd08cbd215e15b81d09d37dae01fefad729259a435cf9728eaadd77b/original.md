```
setdcf()
```

Sets a global decision cost function.  This DCF can be used in `dcf()` and `mindcf()`.   The decision cost function is defined as

```
dcf = ptar Cmiss pmiss + (1-ptar) Cfa pfa.
```

and is defined by the parameters `ptar` (the target prior), `Cfa` (the cost of a false positive) and `Cmiss` (the cost of a false negative.  Arguments:

  * `ptar`. The target prior, default `0.5`.
  * `cfa`.  The cost of a false positive (false alarm), default `1`
  * `cmiss`.  The cost of a false negative (miss), default `1`.

Multiple simultaneous cost functions can be set by specifying any, or a combination, of these parameters as Vectors.

The current values of the parameters of the DCF can be found using `getdcf()`.
