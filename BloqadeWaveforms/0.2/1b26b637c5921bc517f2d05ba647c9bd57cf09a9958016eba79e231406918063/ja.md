```
piecewise_constant_interpolate(wf::Waveform; min_step::Real=0.0, atol::Real = 1.0e-5)
```

`wf`を[`piecewise_constant`](@ref)波形に変換します。これは`min_step`（許容される最小時間ステップ）と許容誤差`atol`に従います。
