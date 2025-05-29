```
TEPperiodic <: TEP
```

周期的ユニットセルのためのTICRA互換の表形式電気特性（TEP）ファイルからのデータを含む構造体。ジオメトリパラメータスイープを含むTEPファイルはまだサポートされていないことに注意してください。

## フィールド

  * `name::String`: 周期的ユニットセルのオブジェクト名。
  * `class::String`: 周期的ユニットセルのクラス名。
  * `theta`: フィールド`atunit`で指定された単位のθ値を含む`AbstractRange`。
  * `phi`: フィールド`atunit`で指定された単位のϕ値を含む`AbstractRange`。
  * `freqs`: 各要素が`Unitful`量である周波数のベクトル。要素はすべて同じ周波数単位を共有する場合もあれば、しない場合もあります。
  * `sff::Array{ComplexF64, 5}`: 前面表面入射の反射係数を含む。
  * `sfr::Array{ComplexF64, 5}`: 後面表面入射の透過係数を含む。
  * `srf::Array{ComplexF64, 5}`: 前面表面入射の透過係数を含む。
  * `srr::Array{ComplexF64, 5}`: 後面表面入射の反射係数を含む。

`s`がフィールド`sff`、`sfr`、`srf`、および`srr`のいずれかを表す場合、`size(s) = (2, 2, length(theta), length(phi), length(freqs))`であり、2×2行列`s[:,:,i,j,k]`は`[sTETE sTETM; sTMTE sTMTM]`の順序で配置されています。

## 参照

  * `TEPscatter`
