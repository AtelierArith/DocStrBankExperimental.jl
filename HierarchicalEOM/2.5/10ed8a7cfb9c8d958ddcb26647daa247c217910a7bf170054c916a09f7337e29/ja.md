```
PowerSpectrum(M, ρ, Q_op, ωlist, reverse; solver, verbose, filename, SOLVEROptions...)
```

周波数領域でのシステムのパワースペクトルを計算します。ここで `P_op` は自動的に `Q_op` の随伴として設定されます。

この関数は次のものと同等です: `PowerSpectrum(M, ρ, Q_op', Q_op, ωlist, reverse; solver, verbose, filename, SOLVEROptions...)`
