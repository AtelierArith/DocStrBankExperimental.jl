```
mutable struct Mixer_2CH
```

2つのアナログ入力をミックスします。デジタル入力の値に応じて入力aまたは入力bのいずれかを選択し、ブレンド時間`t_blend`でソフトスイッチングを実装します。以下のブロックダイアグラムを実装しています: ![mixer_2ch](assets/mixer_2ch.png)。

## フィールド

  * `dt::Float64`
  * `t_blend::Float64`: デフォルト: 1.0
  * `factor_b::Float64`: デフォルト: 0
  * `select_b::Bool`: デフォルト: false

# 例

```julia
using WinchControllers, Test

m2 = Mixer_2CH(0.2, 1.0) # dt=0.2s, t_blend = 1.0s
x = ones(10)
y = 2*x
out = zeros(10)
for i in 1:length(x)
    in1=x[i]
    in2=y[i]
    out[i] = calc_output(m2, x[i], y[i])
    select_b(m2, i > 2)
    on_timer(m2)
end
@test all(out .≈ [1.0, 1.0, 1.0, 1.2, 1.4, 1.6, 1.8, 2.0, 2.0, 2.0])
```
