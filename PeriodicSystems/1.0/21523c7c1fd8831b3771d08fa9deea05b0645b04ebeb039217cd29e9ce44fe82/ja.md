```
pslinfnorm(psys, hinfnorm = false, rtolinf = 0.001, fast = true, offset = sqrt(ϵ)) -> (linfnorm, fpeak)
pshinfnorm(psys, rtolinf = 0.001, fast = true, offset = sqrt(ϵ)) -> (hinfnorm, fpeak)
```

離散時間周期システム `psys = (A(t),B(t),C(t),D(t)` に対して、リフトされた伝達関数行列 `G(λ)` を用いて、`L∞` ノルム `linfnorm` を `pslinfnorm` で、または `H∞` ノルム `hinfnorm` を `pshinfnorm` で計算します（すなわち、`G(λ)` のピークゲイン）と、ピークゲインが達成される対応するピーク周波数 `fpeak` を求めます。`hinfnorm = true` の場合、`H∞` ノルムは `pslinfnorm` で計算されます。

`L∞` ノルムは、`psys` が安定性領域の境界上に極を持つ場合、すなわち単位円上にある場合は無限大になります。`H∞` ノルムは、`psys` が不安定な極を持つ場合に無限大になります。

安定性領域の境界上に極がないことを確認するために、`psys` の極は、モジュリが区間 `[1-β,1+β]` 内にない必要があります。ここで、`β` は安定性領域の境界オフセットです。使用するオフセット `β` は、キーワードパラメータ `offset = β` を介して指定できます。`β` に対して使用されるデフォルト値は `sqrt(ϵ)` であり、ここで `ϵ` は作業用の機械精度です。

キーワード引数 `rtolinf` は、計算された無限ノルムの相対精度を指定します。`rtolinf` に対して使用されるデフォルト値は `0.001` です。

`L∞` ノルムの計算は、[1] で提案されたアルゴリズムに基づいています。特性乗数の計算は、`fast = true` の場合は [2] の高速削減法を用いて、または時間変動次元が存在する場合、`fast = false` の場合は [3] の一般化された周期シュール分解に基づく方法で行われます。

*参考文献*

[1] A. Varga. "Computation of L∞-norm of linear discrete-time periodic systems." Proc. MTNS, Kyoto, 2007.

[2] A. Varga and P. Van Dooren. Computing the zeros of periodic descriptor systems. Systems & Control Letters 50:371–381, 2003.

[3] Kressner, D. An efficient and reliable implementation of the periodic QZ algorithm. IFAC Workshop on Periodic Control Systems (PSYCO 2001), Como (Italy), August 27-28 2001. Periodic Control Systems 2001 (IFAC Proceedings Volumes), Pergamon.
