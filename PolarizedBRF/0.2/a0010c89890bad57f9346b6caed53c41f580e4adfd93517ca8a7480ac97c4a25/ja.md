与えられた角度に対して展開係数を使用して散乱行列を計算します。

```julia
F_from_expansion(coeff, θ; output_dataframe, data)

```

  * `coeff`: 展開係数で、`lmax1 x 6` 行列です。
  * `θ`: 散乱行列が計算される昇順の角度。

オプションのパラメータ:

  * `output_dataframe`: 散乱行列を `DataFrame` 形式で出力するかどうか。デフォルトは `false` で、`Nθ x 6` 行列が出力されます。
  * `data`: 事前に計算されたウィグナー d データを使用します。デフォルトでは新しいデータが計算されます。
