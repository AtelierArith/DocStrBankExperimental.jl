```
mutable struct Event{T <: SSDFloat}
```

個々のイベントのコレクション構造体です。この（可変）構造体は、大量のイベントを処理するのではなく、個々のイベントを調べるために使用されることを意図しています。

## フィールド

  * `locations::VectorOfArrays{CartesianPoint{T}}`: イベントのすべてのヒットの位置のベクトル。
  * `energies::VectorOfArrays{T}`: イベントのヒットに対応するエネルギーのベクトル。
  * `drift_paths::Union{Vector{EHDriftPath{T}}, Missing}`: 各ヒット位置の計算されたドリフトパス。
  * `waveforms::Union{Vector{<:Any}, Missing}`: イベントの生成された信号（波形）。
