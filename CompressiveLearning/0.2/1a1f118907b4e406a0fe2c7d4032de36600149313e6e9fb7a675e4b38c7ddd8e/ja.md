```julia
drawfrequencies(f, d; ...)
drawfrequencies(
    f,
    d,
    σ;
    radial_correction,
    linop_type,
    radialdist
)

```

`d`×`f` 行列（または同等の高速変換）を周波数の描画を行います。

  * `linop_type` は `:dense`、`HDHDHD`、`HGHDHD` または `fastfood` の値を取ることができます。
  * `radialdist` は `drawradiuses` に渡されます。

参照: [`drawradiuses`](@ref).
