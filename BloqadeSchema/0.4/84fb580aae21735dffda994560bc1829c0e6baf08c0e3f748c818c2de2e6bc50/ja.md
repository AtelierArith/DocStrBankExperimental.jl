```
hardware_transform_Δ(Δ,device_capabilities::DeviceCapabilities=get_device_capabilities())
```

与えられたマシンの `device_capabilities` とデチューニング波形 Δ に基づいて、マシンによって実装可能な変換された Δ を返し、元の ($A$) と変換された ($B$) 波形の間の誤差を $\Vert A - B\Vert_1$ として計算します。波形の期間が異なる場合、短い波形は誤差計算のためにゼロでパディングされて期間を等しくします。

# ログ/警告/例外

Δ が次のいずれかの場合、例外がスローされます：

  * [`BloqadWaveforms.Waveform`](@ref) 型ではない
  * 存在しない（`nothing` が渡された）
  * グローバルドライブではない（例：波形のベクトル、ローカライズされた Δ はサポートされていません）
  * `device_capabilities` からの波形に対して許可される最大スロープが無限大に設定されている
  * `device_capabilities` からの波形に対して許可される最小時間ステップがゼロに設定されている

Δ において次のことが発生した場合、デバッグログが発行されます：

  * `device_capabilities` からの時間解像度により、期間が丸められる可能性があります
  * 初期波形がその値のゼロで始まらない/終わらない
  * 波形内の値が `device_capabilities` がサポートする値を超えており、クリッピングする必要があります

# 例

```jldoctest; setup:=(using BloqadeWaveforms)
julia> wf = sinusoidal(duration=2, amplitude=1.3*π);

julia> hardware_transform_Δ(wf)
(Waveform(_, 2.0), 0.06492452289703464)
```
