```
hardware_transform_Ω(Ω,device_capabilities::DeviceCapabilities=get_device_capabilities())
```

与えられたマシンの `device_capabilities` と Rabi 周波数 (Ω) [`Waveform`](@ref) に基づいて、マシンによって実装可能な変換された Ω を返し、元の ($A$) と変換された ($B$) 波形の間の誤差を $\Vert A - B\Vert_1$ として計算します。波形の持続時間が異なる場合、短い波形は誤差計算のためにゼロでパディングされて持続時間を等しくします。

# ログ/警告/例外

Ω が次の条件を満たさない場合、例外がスローされます：

  * [`BloqadWaveforms.Waveform`](@ref) 型ではない
  * 存在しない（`nothing` が渡された）
  * グローバルドライブではない（例：波形のベクトル、ローカライズされた Ω はサポートされていません）
  * `device_capabilities` からの波形に対して許可される最大スロープが無限大に設定されている
  * `device_capabilities` からの波形に対して許可される最小時間ステップがゼロに設定されている

Ω に次のような事象が発生した場合、デバッグログが発行されます：

  * `device_capabilities` からの時間解像度により持続時間が丸められる可能性がある
  * 初期波形がその値のゼロで始まらない/終わらない
  * 波形の値が `device_capabilities` がサポートする値を超えており、クリッピングする必要がある

# 例

```jldoctest; setup:=(using BloqadeWaveforms)
julia> wf = sinusoidal(duration=2, amplitude=1.3*π);

julia> hardware_transform_Ω(wf)
(Waveform(_, 2.0), 2.632451578170084)
```
