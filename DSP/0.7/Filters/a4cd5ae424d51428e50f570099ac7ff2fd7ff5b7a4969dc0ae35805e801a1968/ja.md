```
(N, ωn) = cheb1ord(Wp::Tuple{Real, Real}, Ws::Tuple{Real, Real}, Rp::Real, Rs::Real; domain::Symbol=:z)
```

チェビシェフタイプIフィルタの整数および自然周波数の次数推定。`Wp`と`Ws`はバンドパス/バンドストップケースのための2要素の周波数エッジであり、`Rp`と`Rs`はパスバンドにおけるリップルの最大損失とストップバンドにおける最小リップル減衰をdBで表しています。パスバンドとバンドストップエッジの順序に基づいて、バンドストップまたはバンドパスフィルタのタイプが推測されます。`N`は推定される最低フィルタ次数を示す整数であり、`ωn`はカットオフまたは「-3 dB」周波数を指定します。`:s`のドメインが指定されている場合、パスバンドおよびストップバンド周波数はラジアン/秒として解釈され、アナログフィルタの次数と自然周波数が得られます。デフォルトのドメインは`:z`であり、入力周波数は0から1までの正規化として解釈され、1はπラジアン/サンプルに対応します。
