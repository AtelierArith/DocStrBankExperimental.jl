```
get_v_error(sc::SpeedController)
```

与えられた `SpeedController` インスタンス `sc` の速度誤差を計算して返します。

# 引数

  * sc::[SpeedController](@ref): 速度誤差を計算するための速度制御オブジェクト。

# 戻り値

  * 速度誤差 `v_err` [m/s]。コントローラーが非アクティブな場合、`0.0` を返します。
