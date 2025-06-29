```
(N, ωn) = buttord(Wp::Real, Ws::Real, Rp::Real, Rs::Real; domain=:z)
```

LPF/HPF バターワースフィルタの次数と -3 dB 周波数の近似。`Wp` と `Ws` は通過帯域と阻止帯域の周波数であり、Rp と Rs は通過帯域と阻止帯域のリップル減衰量（dB）です。通過帯域が阻止帯域より大きい場合、フィルタの種類はハイパスフィルタの次数を推定するものと推測されます。`N` は可能な限り低い整数フィルタ次数を指定し、`ωn` はカットオフまたは "-3 dB" 周波数です。`:s` のドメインが指定されている場合、通過帯域と阻止帯域のエッジはラジアン/秒として解釈され、アナログフィルタの次数と自然周波数の結果が得られます。デフォルトのドメインは `:z` で、入力周波数は 0 から 1 までの正規化として解釈され、1 は π ラジアン/サンプルに対応します。
