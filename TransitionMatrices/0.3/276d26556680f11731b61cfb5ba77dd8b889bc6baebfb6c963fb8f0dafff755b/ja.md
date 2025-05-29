```
transition_matrix(s::AbstractAxisymmetricShape{T, CT}, λ, nₘₐₓ, Ng) where {T, CT}
```

与えられた散乱体と波長のためのT行列を計算します。

パラメータ:

  * `s`: 軸対称散乱体。
  * `λ`: 波長。
  * `nₘₐₓ`: T行列の最大次数。
  * `Ng`: 使用するガウス・レジェンドル積分点の数。

戻り値:

  * `𝐓`: T行列を表す`AxisymmetricTransitionMatrix`構造体。
