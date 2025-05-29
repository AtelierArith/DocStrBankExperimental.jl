```
init_qp_green_fft(params::NamedTuple, grid_size::Integer; derivative=false)
```

FFTベースのアルゴリズムの準備ステップ。

# 入力引数

  * `params`: 物理的および数値的パラメータを含む:

      * `alpha`: 擬周期性係数。
      * `k`: 波数。
      * `c`: 関数χの下限カットオフパラメータ。
      * `c_tilde`: 関数χの上限カットオフパラメータ。
      * `epsilon`: 関数Yεのカットオフパラメータ（推奨: `0.4341`）。
      * `order`: 積分のための数値積分の次数。
  * `grid_size`: 次元ごとのグリッドポイントの数（グリッドは `2 * grid_size × 2 * grid_size`）。

# キーワード引数

  * `derivative`: `true`の場合、擬周期的グリーン関数の一次導関数（`∇G`）も計算します。

# 戻り値

```
- `derivative=false`の場合: フィールドを持つNamedTuple
        + `value`: 関数`Ln`のスプライン補間器。
        + `cache`: 後の計算で再利用するための事前計算された積分キャッシュ。
- `derivative=true`の場合: フィールドを持つNamedTuple
        + `value`: 関数`Ln`のスプライン補間器。
        + `grad`: `Ln`の一次導関数のスプライン補間器のタプル（`∂/∂x₁`、`∂/∂x₂`）。
        + `cache`: 後の計算で再利用するための事前計算された積分キャッシュ。
```
