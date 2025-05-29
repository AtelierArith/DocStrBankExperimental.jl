```
sample_clock(wf::Waveform; offset::Real = zero(eltype(wf)), dt::Real = 1e-3)
```

`wf`の持続時間に基づいて時間値の範囲を生成し、各時間値の間に`dt`の時間を持たせ、波形の時間範囲の始まりと終わりに`offset`の時間を追加します。

関連情報は[`sample_values`](@ref)を参照してください。

```jldoctest; setup=:(using BloqadeWaveforms)
julia> wf = sinusoidal(duration=2, amplitude=2π*2.2); # 波形を作成

julia> sample_clock(wf;) # 0.0から2.0までの範囲、ステップは0.001（デフォルト引数）
0.0:0.001:2.0

julia> sample_clock(wf; offset=0.1) # 始まりと終わりを0.1オフセット
0.1:0.001:2.1

julia> sample_clock(wf; dt = 2e-3) # ステップサイズを2e-3に設定
0.0:0.002:2.0
```
