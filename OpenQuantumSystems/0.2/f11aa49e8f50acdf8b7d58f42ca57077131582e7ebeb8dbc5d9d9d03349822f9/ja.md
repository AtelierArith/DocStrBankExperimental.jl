```
getMolStateFC(mol, molElState1, molVibState1, molElState2, molVibState2)
```

[`Molecule`](@ref) の状態のエネルギーを取得します。

# 引数

  * `mol`: [`Molecule`](@ref) のインスタンス。
  * `molElState1`, `molElState2`: ローカル基底における分子の電気状態（すなわち、1または2、ここで1は基底状態）。
  * `molVibState1`, `molVibState2`: 分子の振動状態（例: [1, 5, 2, 2]）。
