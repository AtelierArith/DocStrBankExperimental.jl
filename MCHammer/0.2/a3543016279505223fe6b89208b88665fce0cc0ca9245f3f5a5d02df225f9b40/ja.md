```
  cormat(ArrayName, RankOrder=1)
```

Cormatは、PPMCとランク順の両方を使用して対称相関行列を計算します。ランク順はデフォルトで、これはシミュレーションされた変数の相関に対してIman-Conover法で使用されるものです。

`RankOrder = 1`は、MCHammerで使用されるスピアマン順位相関を計算します（この引数はオプションで、デフォルトはスピアマンです）。

`RankOrder = 0`は、ピアソン積率相関を計算します。
