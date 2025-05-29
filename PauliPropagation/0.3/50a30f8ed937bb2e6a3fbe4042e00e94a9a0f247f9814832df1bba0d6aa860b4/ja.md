```
tiltedtfitrottercircuit(nqubits, n_layers; topology=nothing)
```

傾いた横場イジングモデルのトロッタライズされた回路を返します。 H = Sum*{(i, i+1) in topology} Z*i Z_{i+1} 

  * Sum*{i=1}^{nqubits} Z*i + Sum*{i=1}^{nqubits} X*i

# 引数

  * `nqubits::Integer`: 回路内のキュービットの数。
  * `n_layers::Integer`: 実行するトロッターステップの数。
  * `topology=nothing`: 回路内のキュービットのトポロジー。デフォルト (nothing): 線形チェーン。

# 戻り値

ゲートのベクトルとしてのトロッタライズされた回路。
