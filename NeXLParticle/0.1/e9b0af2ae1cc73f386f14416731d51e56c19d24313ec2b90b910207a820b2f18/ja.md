```
residual(zep::Zeppelin, row::Int, withImgs=false)::Union{Spectrum,Missing}
```

`row`にある粒子の残差スペクトルを返します。存在しない場合はmissingを返します。画像は決して返しません。
