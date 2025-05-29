```
LimitRule(lloq::T, btmax, atmax, nan, rm::Bool) where T <: Real

LimitRule(;lloq = NaN, btmax = NaN, atmax = NaN, nan = NaN, rm::Bool = false)
```

  * `lloq` - LLOQ - low limit of quantification;
  * `btmax` - value for points before Tmax;
  * `atmat` - values for points after Tmax;
  * `nan` - values for replacing `NaN`;
  * `rm` - if `true`, removee all `NaN` points.

Rule for PK subject.

  * STEP 1 (NaN step): replace all `NaN` and `missing` values with nan keyword value (if `nan` not NaN);
  * STEP 2 (LLOQ step): replace values below `lloq` with `btmax` value if this value befor Tmax or with atmax if this value after Tmax (if `lloq` not NaN);
  * STEP 3 (remove NaN): `rm` == true, then remove all `NaN` and `missing` values.

See also: [`applylimitrule!`](@ref)
