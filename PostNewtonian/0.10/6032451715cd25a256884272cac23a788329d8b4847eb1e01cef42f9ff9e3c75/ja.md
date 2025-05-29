```
coorbital_waveform!(storage, inspiral; [ℓₘᵢₙ=2], [ℓₘₐₓ=8], [PNOrder])
coorbital_waveform!(storage, inspiral; [ell_min=2], [ell_max=8], [PNOrder])
```

与えられた `inspiral` 出力を使用して、共軌道フレームでのポストニュートン波形モード重みを評価します。この出力は [`orbital_evolution`](@ref) によって生成され、事前に割り当てられたストレージを使用します。

ストレージは [`coorbital_waveform_computation_storage`](@ref) から返されるオブジェクトであると仮定します。他の引数は [`coorbital_waveform`](@ref) と同じです。
