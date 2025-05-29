```
relative_error(x, x_ref)
```

Compute the relative error between interval `x` and a reference interval `xref`.

### Input

  * `x`    – interval
  * `xref` – reference interval

### Output

An interval representing the relative error (in percentage) of `x` with respect to the reference interval `xref`.

### Algorithm

If $x = [x_L, x_H]$`and``xref = [xref_L, xref_H]``, the output is the interval``y = 100 * [y_L, y_H]``computed as``y_L = -(x_L - xref_L) / den``and``y_H = (x_H - xref_H) / den``, where``den = xref_H - xref_L``.

This function measures the relative error between an interval `x` and a reference interval `x_ref` accounting for it the lower and the upper range bounds separately (see [AlthoffGK18; Eq. (20)](@citet)).
