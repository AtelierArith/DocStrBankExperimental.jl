```
function get_state(m3::Mixer_3CH)
```

コントローラーの状態を整数として返します。

[WinchControllerState](@ref) を整数として返します。

  * wcsLowerForceControl = 0 # 入力 b が選択されました
  * wcsSpeedControl = 1      # 入力 a が選択されました
  * wcsUpperForceControl = 2 # 入力 c が選択されました
