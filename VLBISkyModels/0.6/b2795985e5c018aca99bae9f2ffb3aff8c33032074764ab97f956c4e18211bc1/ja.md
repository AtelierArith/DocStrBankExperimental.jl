```
RadialTruncExp(σ)
```

カットオフ半径1まで指数関数的なプロファイルを持つ放射プロファイルであり、`r<1` の場合、プロファイルは完全にゼロです。

これは次のように評価されます。

```julia
    exp(-(r-1)/σ)
```

## ノート

これは通常、一般的なリングテンプレートを作成するために方位プロファイルと組み合わせて使用されます。

```julia-repl
julia> rad = RadialTruncExp(2.0)
julia> azi = AzimuthalUniform()
julia> t = RingTemplate(rad, azi)
```

## 引数

  * `σ`: 指数的逆減衰パラメータ。
