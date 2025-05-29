```
CameraState(;
    position::VecE2      = VecE2(0.,0.),
    zoom::Real           = 1.,
    rotation::Real       = 0.,
    canvas_width::Int64  = DEFAULT_CANVAS_WIDTH
    canvas_height::Int64 = DEFAULT_CANVAS_HEIGHT
)
```

内部カメラ状態の表現。

  * `position::VecE2`: カメラの(x,y)位置 [メートル] で、x方向は東、y方向は北を測定します。
  * `zoom::Real`: カメラのズームレベル [ピクセル / メートル] で表されます。
  * `rotation::Real`: カメラの回転角度 [ラジアン]。
  * `canvas_width::Int64`: キャンバスの幅 [ピクセル]。
  * `canvas_height::Int64`: キャンバスの高さ [ピクセル]。
