```julia
body_fixed_frame_to_body(mechanism, frame)

```

`frame`が取り付けられている`RigidBody`を返します。

注意: この関数はボディの数に対して線形であり、密なループ内で呼び出すことを意図していません。
