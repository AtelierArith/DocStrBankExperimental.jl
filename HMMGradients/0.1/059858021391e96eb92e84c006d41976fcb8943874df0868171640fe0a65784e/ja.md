`logbackward(Nt,A,y)`

隠れマルコフモデル（HMM）の逆ログ確率（$\hat{\beta}$）を計算します。これは、`Ns` 状態を持つモデルで、ログ遷移行列 `A`（`Ns` × `Ns` 行列である必要があります）、スケール係数、および観測ログ尤度 `y`（`Nt2` × `Ns` サイズで、`Nt2` ≥ `Nt` である必要があります）。
