```julia
log1pexp(x)

```

大きめの `x` に対して慎重に評価された `log(1+exp(x))` を返します。

これは `max(0,x)` の滑らかな近似であるため、["ソフトプラス"](https://en.wikipedia.org/wiki/Rectifier_(neural_networks))変換とも呼ばれます。その逆は [`logexpm1`](@ref) です。

これはデフォルトのパラメータ化における["ソフトプラス"](https://en.wikipedia.org/wiki/Rectifier_(neural_networks))変換とも呼ばれ、`max(0,x)` の滑らかな近似です。

参照:

  * Martin Maechler (2012) [“Accurately Computing log(1 − exp(− |a|))”](http://cran.r-project.org/web/packages/Rmpfr/vignettes/log1mexp-note.pdf)
