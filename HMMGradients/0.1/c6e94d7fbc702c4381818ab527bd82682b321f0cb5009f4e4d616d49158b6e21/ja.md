`logalpha, logML = logforward(Nt,a,A,y)`

隠れマルコフモデル（HMM）のスケーリングされた前向き対数確率（$\hat{\alpha}$）を計算します。`Ns` 状態を持ち、対数遷移行列 `A`（`Ns` × `Ns` 行列である必要があります）、初期対数確率 `a`（`Ns` 長のベクトルである必要があります）、および観測対数尤度 `y`（サイズ `Nt2` × `Ns` で `Nt2` ≥ `Nt` である必要があります）。

返されるもの：

  * `logalpha` 前向き対数確率を含むサイズ `(Nt,Ns)` の行列
  * `logML` 観測の対数尤度で、系列の長さで正規化されています。すなわち、$\log(P(\mathbf{X}))/N_t$。

`logalpha, logML = logforward(Nt,t2tr,A,y)`

制約された経路での前向き対数確率を返します（[`forward`](@ref)を参照）。
