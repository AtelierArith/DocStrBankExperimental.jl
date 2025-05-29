```
level_spacing_cdf(spect::UnfoldedSpectrum, pts::Vector; n::Int = 1) → s::Vector w::Vector
```

レベル間隔の累積密度関数を、位置 `pts` で評価して返します。最近接隣接レベル間隔はデフォルトで、n=1 によって与えられます。

## 引数

  * `spect`: 型 [`UnfoldedSpectrum`](@ref) のインスタンスとして与えられる展開されたエネルギースペクトル。
  * `pts`: 累積密度関数を評価する位置。

## キーワード引数

  * `n=1` : レベル間隔の順序。

## 戻り値

  * `w` : 累積確率のベクトル。
