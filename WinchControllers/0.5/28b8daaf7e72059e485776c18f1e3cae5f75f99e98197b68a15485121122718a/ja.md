```
get_state(wc::WinchController) -> @enum WinchControllerState
```

指定された `WinchController` インスタンス `wc` の現在の状態を返します。返される値は、通常、ウインチコントローラーの動作状態やステータス（位置、速度、エラーステータスなど）を表します。

# 引数

  * `wc::WinchController`: 状態を取得するウインチコントローラーオブジェクト。

# 返り値

  * @enum [WinchControllerState](@ref)
