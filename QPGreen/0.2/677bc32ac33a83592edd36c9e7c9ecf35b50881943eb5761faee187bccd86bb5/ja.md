```
eval_smooth_qp_green(x, params::NamedTuple, value_interpolator, Yε_cache::IntegrationCache; nb_terms=50)
```

滑らかなα準周期的グリーン関数$G_0(x)$を計算します（すなわち、FFTベースの手法[Zhang2018](@cite)を使用して、項$H_0^{(1)(k|x|)}$なしで、級数展開のフォールバックを使用します）。

# 入力引数

  * `x`: グリーン関数を評価する2D点。
  * `params`: 物理的および数値的パラメータを含むNamedTuple：

      * `alpha`: 準周期性係数
      * `k`: 波数
      * `c`: 関数`χ`の下限カットオフパラメータ。
      * `c_tilde`: 関数`χ`の上限カットオフパラメータ。
      * `epsilon`: 関数`Yε`のカットオフパラメータ（推奨値: `0.4341`）。
      * `order`: 数値積分の次数
  * `value_interpolator`: `Ln`のためのバイキュービックスプライン補間器。
  * `Yε_cache`: カットオフ関数`Yε`の評価のための事前計算されたキャッシュ。

# キーワード引数

  * `nb_terms`: 固有関数展開のフォールバックに使用する項の数（`x₂ ∉ [-c, c]`の場合）

# 戻り値

  * `G_0`: 点`x`における準周期的グリーン関数の近似値
