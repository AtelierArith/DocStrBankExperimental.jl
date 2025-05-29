```
PupilFunction(nₐ::Real, λ::Real, n::Real, 
              zc::ZernikeCoefficients;
              grid_size::Int=64)
```

ZernikeCoefficients型からPupilFunctionを作成します。

# 引数

  * `nₐ`: 数値開口
  * `λ`: マイクロメートル単位の波長
  * `n`: 屈折率
  * `zc`: 振幅および位相係数を含むZernikeCoefficients

# キーワード引数

  * `grid_size`: 正方形サンプリンググリッドのサイズ（デフォルト: 64）

# 戻り値

  * Zernike多項式から計算された複素場を持つ`PupilFunction`
