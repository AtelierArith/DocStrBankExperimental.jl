```
RadialGaussian(σ)
```

半径が1で標準偏差 `σ` の放射状ガウスリングのプロファイルを作成します。

## 注意事項

これは通常、一般的なリングテンプレートを作成するために方位プロファイルと組み合わせて使用されます。

```julia-repl
julia> rad = RadialGaussian(0.1)
julia> azi = AzimuthalUniform()
julia> t = RingTemplate(rad, azi)
```

## 引数

  * `σ`: ガウスリングの標準偏差。
