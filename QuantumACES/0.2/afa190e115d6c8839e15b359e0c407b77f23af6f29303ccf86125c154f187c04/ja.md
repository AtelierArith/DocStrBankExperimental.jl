```
update_noise(d::Design, noise_param::AbstractNoiseParameters)
update_noise(d::Design, gate_probabilities::Dict{Gate, Vector{Float64}})
```

`d`のコピーを返します。回路は`noise_param`に従って生成されたノイズ、またはゲート確率`gate_probabilities`で更新されています。
