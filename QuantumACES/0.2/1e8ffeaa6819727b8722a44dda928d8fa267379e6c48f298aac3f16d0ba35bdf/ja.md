```
update_noise(c::AbstractCircuit, noise_param::AbstractNoiseParameters)
update_noise(c::AbstractCircuit, gate_probabilities::Dict{Gate, Vector{Float64}})
```

`c`のコピーを返し、回路は`noise_param`に従って生成されたノイズ、またはゲート確率`gate_probabilities`で更新されます。
