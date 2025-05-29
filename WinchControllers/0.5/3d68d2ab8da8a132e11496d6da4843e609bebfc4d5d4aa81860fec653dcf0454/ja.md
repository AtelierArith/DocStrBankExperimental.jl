```
mutable struct Integrator
```

外部リセットを持つ離散積分器。

## フィールド

  * `dt::Float64`
  * `i::Float64`: デフォルト: 1.0
  * `output::Float64`: デフォルト: 0.0
  * `last_output::Float64`: デフォルト: 0.0

# 例

```julia
int = Integrator(0.05, 2, 3)      # dt, 積分定数, 初期出力  
input = 2
for i in 1:3
    out = calc_output(int, input) # 出力を計算
    println(out)
    on_timer(int)                 # 各タイムステップで呼び出す必要があります
end
reset(int, 3)                     # 積分器を初期状態にリセット
```
