```
level_spacing_pdf(spect::UnfoldedSpectrum, bins::Vector; n::Int = 1) → s::Vector p::Vector
```

レベル間隔の確率密度関数のヒストグラムを返します。最近接隣接レベル間隔はデフォルトで、n=1によって与えられます。

## 説明

最近接隣接レベル間隔分布は、最も一般的に研究されるスペクトル統計です。

## 引数

  * `spect`: 型[`UnfoldedSpectrum`](@ref)のインスタンスとして与えられる展開されたエネルギースペクトル。
  * `bins`: ビン位置の境界。

## キーワード引数

  * `n=1` : レベル間隔の順序。

## 戻り値

  * `p` : 各ビンに含まれる確率のベクトル。
