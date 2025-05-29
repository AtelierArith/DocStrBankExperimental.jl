```
mutable struct UnitDelay
```

UnitDelayは、入力信号を1タイムステップ遅延させます。

## フィールド

  * `last_output::Float64`: デフォルト: 0
  * `last_input::Float64`: デフォルト: 0

# 例

```julia
ud = UnitDelay()
for i in 1:3
    out = calc_output(ud, i) # 入力を更新し、出力を計算します
    println(out)
    on_timer(ud)             # 次のタイムステップ
end
```
