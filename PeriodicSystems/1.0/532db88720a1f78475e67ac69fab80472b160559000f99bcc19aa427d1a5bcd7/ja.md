```
 ps2spls(psys::PeriodicStateSpace[, kstart]; cyclic = false) -> sys::DescriptorStateSpace
```

離散時間周期システムに相当するリフトされたLTIシステムを構築します。

周期 `T` とサンプル時間 `Ts` を持つ離散時間周期システム `psys = (A(t),B(t),C(t),D(t))` に対して、入力、状態、出力ベクトルが長さ `T` の時間間隔で定義された等価なスタックされた（[1]を参照）LTI記述状態空間表現 `sys = (As-λEs,Bs,Cs,Ds)` が構築されます。オプションの引数 `kstart` は周期行列のシーケンスを開始する希望の時間を指定します（デフォルト: `kstart = 1`）。行列 `As`、`Es`、`Bs`、`Cs` および `Ds` は、[SparseArrays.jl](https://github.com/JuliaSparse/SparseArrays.jl) パッケージ内で定義された疎行列です。

`cyclic = true` の場合、[2] の循環再定式化が使用され、入力、状態、出力ベクトルが長さ `T` の時間間隔で定義されたリフトされた標準システムが構築されます。

*参考文献*

[1] O. M. Grasselli and S. Longhi. Finite zero structure of linear periodic discrete-time systems.      Int. J. Systems Sci., 22:1785–1806,  1991.

[2] D. S. Flamm. A new shift-invariant representation for periodic systems,      Systems and Control Letters, 17:9–14, 1991.
