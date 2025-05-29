```
 ps2ls(psys::PeriodicStateSpace[, kstart]; ss = false, cyclic = false) -> sys::DescriptorStateSpace
```

離散時間周期システムに相当する離散時間リフトLTIシステムを構築します。

周期 `T` とサンプル時間 `Ts` を持つ離散時間周期システム `psys = (A(t),B(t),C(t),D(t))` に対して、入力、状態、出力ベクトルが長さ `T` の時間間隔で定義される等価なスタックされた（[1]を参照）LTI記述状態空間表現 `sys = (A-λE,B,C,D)` が構築されます。オプションの引数 `kstart` は、周期行列のシーケンスを開始する希望の時間を指定します（デフォルト: `kstart = 1`）。

`ss = true`（デフォルト: `ss = false`）の場合、すべての非動的モードが排除され、標準状態空間実現（`E = I`）が決定されます。これは、入力と出力ベクトルが長さ `T` の時間間隔で定義されるリフティング技術に対応します[2]。標準リフト表現の決定には行列積の形成（例えば、モノドロミー行列を明示的に形成することによって）が含まれ、したがって数値計算にはあまり適していない可能性があります。

`cyclic = true` の場合、[3]のサイクリック再定式化が使用され、入力、状態、出力ベクトルが長さ `T` の時間間隔で定義されるリフト標準システムが構築されます。

*参考文献*

[1] O. M. Grasselli and S. Longhi. Finite zero structure of linear periodic discrete-time systems.      Int. J. Systems Sci., 22:1785–1806,  1991.

[2] R. A. Meyer and C. S. Burrus. A unified analysis of multirate and periodically time-varying     digital filters”, IEEE Transactions on Circuits and Systems, 22:162–167, 1975.

[3] D. S. Flamm. A new shift-invariant representation for periodic systems,      Systems and Control Letters, 17:9–14, 1991.
