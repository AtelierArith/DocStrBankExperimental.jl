エネルギースペクトルプロットを作成します。スカラー波数レベル $\kappa \in \mathbb{N}$ におけるエネルギーは次のように定義されます。

$$
\hat{e}(\kappa) = \int_{\kappa \leq \| k \|_2 < \kappa + 1} | \hat{e}(k) | \mathrm{d} k,
$$

San と Staples によると [San2012](@cite)。

キーワード引数：

  * `sloperange = [0.6, 0.9]`: スロープがプロットされる x 軸の割合（0 と 1 の間）。
  * `slopeoffset = 1.3`: エネルギースペクトルの上に慣性スロープがプロットされる距離。
  * `kwargs...`: [`observespectrum`](@ref) に渡されます。
