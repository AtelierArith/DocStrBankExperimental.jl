```
mean(imf::Distributions.ContinuousUnivariateDistribution; kws...) =
    quadgk(x->x*pdf(imf,x), extrema(imf)...; kws...)[1]
```

提供された `imf` 分布の平均を計算するシンプルなワンライナーで、渡されたキーワード引数 `kws...` を使用して `QuadGK.quadgk` による数値積分を行います。これは一般的なフォールバックであり、IMFモデルに対して明示的に定義する方が良いです。`pdf(imf,x)` と `extrema(imf)` が定義されている必要があります。
