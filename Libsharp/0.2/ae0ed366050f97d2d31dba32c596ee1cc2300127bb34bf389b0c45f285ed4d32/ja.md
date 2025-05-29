```
make_triangular_alm_info(lmax::Integer, mmax::Integer, stride::Integer)
```

Healpix*cxxで使用されるスキームに従って、a*lmデータ構造を初期化します。

# 引数

  * `lmax::Integer`: 最大球面調和ℓ
  * `mmax::Integer`: 最大球面調和m
  * `stride::Integer`: リング内の連続するピクセル間のストライド

# 戻り値

  * `AlmInfo`オブジェクト
