```
inertial_waveform!(storage, inspiral; [ℓₘᵢₙ=2], [ℓₘₐₓ=8], [PNOrder])
inertial_waveform!(storage, inspiral; [ell_min=2], [ell_max=8], [PNOrder])
```

与えられた `inspiral` 出力によって [`orbital_evolution`](@ref) を使用して、慣性フレームでのポストニュートン波形モードの重みを評価します。ストレージは [`inertial_waveform_computation_storage`](@ref) から返されるオブジェクトであると仮定します。他の引数は [`inertial_waveform`](@ref) と同じです。
