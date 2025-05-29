```
sample_values(wf::Waveform, clocks; offset::Real = zero(eltype(wf)))
sample_values(wf::Waveform; offset::Real = zero(eltype(wf)), dt::Real = 1e-3)
```

波形 `wf` のサンプル値は、サンプリングするための正確な時間値を含む反復可能な `clocks` を提供するか、波形の時間範囲の開始と終了に加えるオフセットを指定する `offset` と時間値間のステップを指定する `dt` の値を提供することによって取得できます。

詳細は [`sample_clock`](@ref) を参照してください。

```jldoctest; setup:=using(using BloqadeWaveforms)
julia> wf = linear_ramp(duration=0.5, start_value=0.0, stop_value=2π*1.0);

julia> sample_values(wf,0.0:0.1:0.5) # サンプル波形値を範囲から取得
6-element Vector{Float64}:
 0.0
 1.2566370614359172
 2.5132741228718345
 3.7699111843077517
 5.026548245743669
 6.283185307179586

julia> sample_values(wf; dt=5e-2) # サンプリングされた値の間の時間ギャップは5e-2
11-element Vector{Float64}:
 0.0
 0.6283185307179586
 1.2566370614359172
 1.8849555921538759
 2.5132741228718345
 3.141592653589793
 3.7699111843077517
 4.39822971502571
 5.026548245743669
 5.654866776461628
 6.283185307179586

```
