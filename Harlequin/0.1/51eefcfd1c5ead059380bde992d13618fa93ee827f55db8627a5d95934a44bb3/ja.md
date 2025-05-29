```
update_nobs_matrix!(nobs_matrix::Vector{NobsMatrixElement{T}}, psi_angle, sigma_squared, pixidx, flagged)
```

KurkiSuonio2009の式(10)をTODのサンプルに対して反復的に適用して、`nobs_matrix`内の行列$M_p$を更新します。パラメータの意味は以下の通りです：

  * `nobs_matrix`はこの関数によって更新される構造体です
  * `psi_angle`は`N`要素の配列で、偏光角（ラジアン単位）を含みます
  * `sigma_squared`は`N`要素の配列で、TODのサンプルに対するσ^2の値をそれぞれ含みます
  * `pixidx`は`N`要素の配列で、TODによって観測されたピクセルインデックスを含みます
  * `flagged`は`N`要素のブール配列で、`true`はTODのサンプルがマップを生成するために使用されるべきではないことを意味します。これはジャックナイフを生成したり、TOD内の動く物体を無視するために使用できます
