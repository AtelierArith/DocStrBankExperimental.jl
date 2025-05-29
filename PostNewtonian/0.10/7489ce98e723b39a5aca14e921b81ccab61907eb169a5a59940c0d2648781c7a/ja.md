```
coorbital_waveform_computation_storage(inspiral; [ℓₘᵢₙ=2], [ℓₘₐₓ=8], [PNOrder])
coorbital_waveform_computation_storage(inspiral; [ell_min=2], [ell_max=8], [PNOrder])
```

コオルビタルフレームで波形を計算するために必要なストレージを、アロケーションなしで構築します。

これにより、波形自体と一時的なストレージとして使用される `PNSystem` のストレージが返されます。返された量は、アンパックせずに [`coorbital_waveform!`](@ref) の最初の引数として渡すことができます。

引数の意味は [`coorbital_waveform`](@ref) と同じです。
