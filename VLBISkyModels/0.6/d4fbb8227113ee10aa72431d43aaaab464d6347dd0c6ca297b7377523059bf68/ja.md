```
RadialDblPower(αinner, αouter)
```

二重冪法則によって与えられる放射プロファイルで、関数の形は

```julia
    r^αinner*inv(1+ r^(αinner + αouter + 1))
```

## 注意事項

これは通常、一般的なリングテンプレートを作成するために方位プロファイルと組み合わされます。

```julia-repl
julia> rad = RadialDblPower(3.0, 3.0)
julia> azi = AzimuthalUniform()
julia> t = RingTemplate(rad, azi)
```

## 引数

  * `αinner` `r<1` のための冪法則の指数。
  * `αouter` `r≥1` のための冪法則の指数。
