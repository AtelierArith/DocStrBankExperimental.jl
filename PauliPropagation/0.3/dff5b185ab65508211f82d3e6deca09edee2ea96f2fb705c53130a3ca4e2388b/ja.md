```
truncatemincoeff(coeff, min_abs_coeff::Real)
```

`abs(coeff) < min_abs_coeff` の場合は `true` を返します。係数の切り捨ては、型に適用できない場合はデフォルトで false にする必要があります。
