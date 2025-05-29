```
generate_dos(bands::Bands, kpoints::Array{KPoint, 1};
    smear::Function=gaussian, energy_number::Integer=10000)
```

バンドとk点を使用して電子密度状態を生成します。

# 引数

  * `bands::Bands`: バンドのメタデータ
  * `kpoints::Array{KPoint, 1}`: k点のメタデータ
  * `smear::Function=gaussian`: スミアリング関数、デフォルト: ガウススミア
  * `energy_number::Integer=10000`: エネルギーポイントの数、デフォルト 10000

# 戻り値

  * `dos::DOS`: dosのメタデータ
