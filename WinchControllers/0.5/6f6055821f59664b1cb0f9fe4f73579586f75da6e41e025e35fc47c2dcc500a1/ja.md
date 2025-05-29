```
mutable struct Mixer_3CH
```

3つのアナログ入力をミックスします。デジタル入力の値に応じて入力a、入力b、または入力cのいずれかを選択し、ブレンド時間`t_blend`を用いてソフトスイッチングを実装します。以下のブロックダイアグラムを実装します: ![mixer_3ch](assets/mixer_3ch.png)。

## フィールド

  * `dt::Float64`
  * `t_blend::Float64`: デフォルト: 1.0
  * `factor_b::Float64`: デフォルト: 0
  * `factor_c::Float64`: デフォルト: 0
  * `select_b::Bool`: デフォルト: false
  * `select_c::Bool`: デフォルト: false

# 例

```julia
using WinchControllers, ControlPlots

TIME = range(0.0, 10, 501)
SIN1 = sin.(TIME * 0.5 * 2pi) * 2
SIN2 = sin.(TIME * 0.25 * 2pi)
NOISE = (rand(501).-0.5) * 2
mix3 = Mixer_3CH(10, 0.25)
out  = zeros(501)

for i in 1:501                   # 10s with dt=0.02
    if i == 150
        select_b(mix3, true)
    elseif i == 300
        select_c(mix3, true)
    elseif i == 450
        select_c(mix3, false)        
    end
    out[i] = calc_output(mix3, SIN1[i], SIN2[i], NOISE[i])
    on_timer(mix3)
end
plot(TIME, out)
```
