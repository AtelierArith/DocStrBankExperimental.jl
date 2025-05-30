```
makehomogeneous(mag::NIVolume; sigma_mm=7, nbox=15)
```

NIfTIファイルからのNIVolumeの均一性補正。

### キーワード引数:

  * `sigma_mm`: バイアスフィールドを得るための平滑化のためのシグマサイズ。NIfTIボクセルサイズを考慮に入れます。
  * `nbox`: ボックスセグメンテーションステップの各次元におけるボックスの数。
