```
FermiFSIndex
```

[`FermiFS`](@ref)上でのインデックス作成と[`excitation`](@ref)の実行に使用される構造体。

## フィールド:

  * `occnum`: 占有数。
  * `mode`: モードのインデックス。
  * `offset`: アドレスにおけるモードの位置。ビットストリングでアドレスが表されるときは`mode - 1`であり、`SortedParticleList`を使用する場合はリスト内の位置。
