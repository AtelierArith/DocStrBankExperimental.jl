静的構造因子補正を与えられた展開係数に適用します。

```julia
ssf_correction(
    coeff,
    Cext,
    Csca;
    volume_fraction,
    r,
    τ,
    Nθ,
    Nm,
    equidistant,
    output_dataframe,
    strategy,
    kwargs...
)

```

  * `coeff`: 元の展開係数、`(lmax + 1) x 6` 行列。
  * `Cext`: 消失断面積。
  * `Csca`: 散乱断面積。

オプションのパラメータ:

  * `volume_fraction`: 散乱体が占める体積分率。デフォルトは `0.2`。
  * `r`: 散乱体の体積的に等価な/有効半径。
  * `τ`: 粘着因子。デフォルトは `0` で、粘着性は考慮されません。有効範囲は `τ ≥ (2 - √2) / 6`。
  * `Nθ`: 出力散乱行列に必要な角度の数。デフォルトは `181`。
  * `Nm`: 中間ステップで使用される角度の数。デフォルトは `2lmax`。
  * `equidistant`: 出力角度が等間隔であるべきかどうか。デフォルトは `true`。`false` に設定すると、ガウス求積ノード（cosθ用）が代わりに使用されます。
  * `output_dataframe`: 散乱行列を `DataFrame` 形式で出力するかどうか。デフォルトは `false` で、`Nθ x 6` 行列が出力されます。
  * `strategy`: 展開のための特別な戦略。デフォルトは `PolarizedBRF.StandardExpansion` で、展開は `expand()` に指定されたキーワード引数を介して制御できます。`PolarizedBRF.Ito18` を使用すると、Ito et al. (2018) で使用された戦略が代わりに使用され、最高の展開レベルは `4 * lmax` に設定され、展開係数は閾値 `1e-8` でカットオフされます。
  * `expand()` のすべてのキーワード引数もここに適用されます。
