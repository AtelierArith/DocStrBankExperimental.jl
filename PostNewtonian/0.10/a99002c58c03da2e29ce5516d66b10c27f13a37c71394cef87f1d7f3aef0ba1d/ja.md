```
inertial_waveform_computation_storage(inspiral; [ℓₘᵢₙ=2], [ℓₘₐₓ=8], [PNOrder])
inertial_waveform_computation_storage(inspiral; [ell_min=2], [ell_max=8], [PNOrder])
```

割り当てなしで慣性フレーム内の波形を計算するために必要なストレージを構築します。

これにより、波形自体のストレージ、Wigner 𝔇 行列を計算するために使用されるストレージ、および「インプレース」乗算のためのストレージが返されます。返される量は、アンパックせずに [`inertial_waveform!`](@ref) の最初の引数として渡すことができます。

引数の意味は [`inertial_waveform`](@ref) と同じです。
