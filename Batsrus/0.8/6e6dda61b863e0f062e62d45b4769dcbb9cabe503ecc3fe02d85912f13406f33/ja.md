```
 get_timeseries(files::AbstractArray, loc; tstep = 1.0)
```

PIC出力`files`から`loc`で最近傍法を用いてプラズマモーメントとEM場を抽出します。現在のところ、2D出力のみに対応しています。単一ポイント変数が必要な場合は、[`interp1d`](@ref)を参照してください。
