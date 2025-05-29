```
add_low_frequency_disturbance(sys::StateSpace; ϵ = 0, measurement = false)
add_low_frequency_disturbance(sys::StateSpace, Cd; ϵ = 0, measurement = false)
```

`sys`に低周波（`ϵ=0`の場合は積分）擾乱モデルを追加します。積分入力擾乱がオブザーバーと一緒に使用される場合、コントローラーは積分作用を持ちます。

  * `Cd`: 入力擾乱を追加する場合、この行列は擾乱状態が`sys`の状態にどのように影響するかを示し、デフォルトでは`sys.B`になります。`measurement=true`の場合、この行列は擾乱状態が`sys`の出力にどのように影響するかを示し、デフォルトでは`I(sys.ny)`になります。

# 引数:

  * `ϵ`: 積分器の極を安定領域に`ϵ`だけ移動します。
  * `measurement`: trueの場合、擾乱は測定擾乱であり、そうでない場合は入力擾乱です。
