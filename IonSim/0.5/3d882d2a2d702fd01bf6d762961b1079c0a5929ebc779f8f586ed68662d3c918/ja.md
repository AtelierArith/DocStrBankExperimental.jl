```
groundstate(obj)
```

もし obj が `VibrationalMode` の場合、そのモードの N=0 ケットを返します。もし obj が `VibrationalMode` のベクトルの場合、与えられた順序で `mode1[0] ⊗ mode2[0] ⊗ ...` のテンソル積を返します。もし obj が `LinearChain` の場合、運動自由度の完全な基底状態をテンソル積として返します。
