```julia
Transform(position_transform, velocity_transform, from, to)

```

`Transform` インスタンスの外部コンストラクタです。位置と速度の変換、および初期および最終の参照フレームを関数引数を介して提供します。これは `Transform{InitialFrame, FinalFrame}(position_transform, velocity_transform)` の代替構文です。
