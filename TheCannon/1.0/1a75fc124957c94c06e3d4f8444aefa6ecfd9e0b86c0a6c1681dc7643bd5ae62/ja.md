infer(flux, ivar, theta, scatters; quadratic=true, verbose=true)

キャノンのテストステップを実行します。与えられた `theta` と `scatters`（トレーニングから）、星のパラメータを推定します。

  * `flux` には、ラベルを推定したい各星のスペクトルが含まれています。トレーニングセット内で、`nstars x npixels` の形状である必要があります（行ベクトルはスペクトルです）。
  * `ivar` には、`flux` と同じ形状の各ピクセルの逆分散が含まれています。
  * `theta`: キャノン係数を含む行列です。`n_expanded_labels x npix` の形状になります。
  * `scatters`: 各ピクセルでのモデルの散乱です。

`verbose` が true に設定されている場合、処理された100星ごとに更新が表示されます。
