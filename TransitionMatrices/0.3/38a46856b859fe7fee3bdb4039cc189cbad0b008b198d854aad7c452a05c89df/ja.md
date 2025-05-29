```
transition_matrix_iitm(s::AbstractAxisymmetricShape{T, CT}, λ, nₘₐₓ, Nr, Nϑ; rₘᵢₙ) where {T, CT}
```

IITMを使用して、与えられた散乱体と波長のT行列を計算します。

パラメータ：

  * `s`: 軸対称散乱体。
  * `λ`: 波長。
  * `nₘₐₓ`: T行列の最大次数。
  * `Nr`: 使用する放射状の数値積分点の数。
  * `Nϑ`: 使用する天頂の数値積分点の数。

キーワード引数：

  * `rₘᵢₙ`: 放射状の数値積分の開始点。デフォルトは `rmin(s)` で、最大内接球の半径です。

戻り値：

  * `𝐓`: T行列を表す `AxisymmetricTransitionMatrix` 構造体。
