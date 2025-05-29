```
nside2npix(nside::Integer) -> Integer
```

指定された `NSIDE` 値の Healpix マップのピクセル数を返します。`NSIDE` が整数の2の累乗でない場合、関数は `DomainError` 例外をスローします。
