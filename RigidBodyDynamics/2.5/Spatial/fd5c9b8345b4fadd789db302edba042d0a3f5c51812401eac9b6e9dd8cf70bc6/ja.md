```julia
transform(
    accel,
    old_to_new,
    twist_of_current_wrt_new,
    twist_of_body_wrt_base
)

```

`SpatialAcceleration`を別のフレームに変換します。

変換ルールは、ツイストの変換ルールを微分することによって得られます。
