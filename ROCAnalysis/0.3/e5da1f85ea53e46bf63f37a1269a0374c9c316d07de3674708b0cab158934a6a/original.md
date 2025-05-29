```
dcf()
```

Computes the classical decision cost function:

```
dcf = ptar Cmiss pmiss + (1-ptar) Cfa pfa.
```

The *relative* value of the cost function is only determined by the ratio

```
oeff = (ptar / (1 - ptar)) * (Cmiss / Cfa).
```

Therefore, this function is computed using `ber()` and scaling accordingly.  Arguments:

  * `tar`, `non`: target and non-target scores
  * `tnt::TNT`: a `TNT` object containing target and non-target scores.
  * `r::Roc`: a `Roc` object, the result of `roc()`
  * `; d::DCF`: a decision cost function, default `getdcf()`.  This can be a vector or DCFs.
  * `; thres`: the threshold used to make decisions, default `-plo(d)`
  * `; norm`: are the costs normalized to a trivial system deciding using the prior only, default: `false`
