```
AzimuthalUniform()
AzimuthalUniform{T}()
```

すべての角度に対して均一な方位プロファイルです。

## 注意事項

これは通常、一般的なリングテンプレートを作成するために放射状プロファイルと組み合わせて使用されます。

```julia-repl
julia> rad = RadialDblPower(3.0, 3.0)
julia> azi = AzimuthalUniform() # デフォルトはFloat64
julia> t = RingTemplate(rad, azi)
```
