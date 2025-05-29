```
applylimitrule!(data::Union{PKSubject, PDSubject}, rule::LimitRule)
```

Apply rule to PK subject .

  * STEP 1 (NaN step): replace all `NaN` and `missing` values with nan keyword value (if `nan` not NaN);
  * STEP 2 (LLOQ step): replace values below `lloq` with `btmax` value if this value befor Tmax or with atmax if this value after Tmax (if `lloq` not NaN);
  * STEP 3 (remove NaN): `rm` == true, then remove all `NaN` and `missing` values.
